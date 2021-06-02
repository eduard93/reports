FROM intersystemsdc/iris-community:2020.4.0.547.0-zpm

USER ${ISC_PACKAGE_MGRUSER}

COPY iris.script iris.script

RUN iris start IRIS \
    && iris session IRIS < iris.script \
    && iris stop IRIS quietly