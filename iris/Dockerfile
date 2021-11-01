FROM intersystemsdc/iris-community:2021.1.0.215.3-zpm

USER ${ISC_PACKAGE_MGRUSER}

COPY iris.script iris.script

RUN iris start IRIS \
    && iris session IRIS < iris.script \
    && iris stop IRIS quietly
