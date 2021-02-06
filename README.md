<!--
{% comment %}
Licensed to the Apache Software Foundation (ASF) under one or more
contributor license agreements.  See the NOTICE file distributed with
this work for additional information regarding copyright ownership.
The ASF licenses this file to you under the Apache License, Version 2.0
(the "License"); you may not use this file except in compliance with
the License.  You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
{% endcomment %}
-->
# Apache Calcite -- Avatica

The purpose of this fork is to solve a specific issue querying data in Apache Druid from Tableau, where weekday names are incorrectly presented due to Tableau expecting `Sunday=1, ..., Saturday=7` and Druid using the `Monday=1, ..., Sunday=7` scheme. The "fix" is accomplished by modifying SQL string passed into `AvaticaStatement.executeInternal` method, wrapping weekday related functions into a SQL CASE statement, which adjust the numeric values returned by Druid to Tableau's liking.

To build the shaded JDBC jar - clone this repository and issue the following in the repository root folder:  
  
**Mac/Unix:**  
> ./gradle build -p shaded -Prelease
  
**Windows:**  
> gradlew build -p shaded -Prelease
  
