# Copyright 2023 Adobe Systems Incorporated
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM cypress/included:13.14.1

ENV APP_PATH /usr/src/app
RUN wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | tee /etc/apt/trusted.gpg.d/google.asc >/dev/null
RUN apt -qqy update \
    # Generic dependencies
    && apt -qqy --no-install-recommends install \
    curl \
    build-essential

# Set Application Environment
WORKDIR ${APP_PATH}
COPY ./test-module ./
RUN npm install
# no need to wait for selenium
ENTRYPOINT ["bash","run.sh"]

