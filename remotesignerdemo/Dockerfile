FROM --platform=linux/amd64 cimg/android:2023.09.1-ndk as build

COPY . /home/gradle/src

USER root

WORKDIR /home/gradle/src

RUN gradle remotesignerdemo:buildFatJar --no-daemon

FROM openjdk:17.0.2-jdk-slim-bullseye

COPY --from=build /home/gradle/src/remotesignerdemo/build/libs/*.jar /app/remotesignerdemo.jar

ENTRYPOINT ["java","-jar","/app/remotesignerdemo.jar"]