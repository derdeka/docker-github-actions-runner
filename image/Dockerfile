FROM ghcr.io/actions/actions-runner:2.300.2 as actions-runner

FROM cypress/browsers:node18.12.0-chrome107

ENV RUNNER_ALLOW_RUNASROOT=1
ENV RUNNER_MANUALLY_TRAP_SIG=1
ENV ACTIONS_RUNNER_PRINT_LOG_TO_STDOUT=1

ENV AGENT_TOOLSDIRECTORY=/opt/hostedtoolcache
RUN mkdir -p /opt/hostedtoolcache

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

WORKDIR /actions-runner

COPY --from=actions-runner /actions-runner .

COPY token.sh entrypoint.sh app_token.sh /
RUN chmod +x /token.sh /entrypoint.sh /app_token.sh

ENTRYPOINT ["/entrypoint.sh"]
CMD ["./bin/Runner.Listener", "run", "--startuptype", "service"]
