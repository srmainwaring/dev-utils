# Copyright 2022 Proyectos y Sistemas de Mantenimiento SL (eProsima).
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

set(TEST_NAME PeriodicEventHandlerTest)

set(TEST_SOURCES
        PeriodicEventHandlerTest.cpp
        ${PROJECT_SOURCE_DIR}/src/cpp/event/PeriodicEventHandler.cpp
        ${PROJECT_SOURCE_DIR}/src/cpp/event/logging/LogEventHandler.cpp
        ${PROJECT_SOURCE_DIR}/src/cpp/event/logging/LogSevereEventHandler.cpp
        ${PROJECT_SOURCE_DIR}/src/cpp/testing/LogChecker.cpp
    )
all_library_sources("${TEST_SOURCES}")

set(TEST_LIST
        trivial_create_handler
        wait_handler
        handler_period
        handler_period_without_callback
        limit_cases
        negative_cases
        not_wait_in_destruction
    )

set(TEST_EXTRA_LIBRARIES
        fastcdr
        fastdds
        cpp_utils
    )

add_unittest_executable(
    "${TEST_NAME}"
    "${TEST_SOURCES}"
    "${TEST_LIST}"
    "${TEST_EXTRA_LIBRARIES}")
