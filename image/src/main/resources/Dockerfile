FROM openexperiencecloud.jfrog.io/docker/cloud.openexperience.content.images.base:1.0.0-SNAPSHOT

ENV COMPOSITE_SEED_FEATURES="/opt/oec/setup/features/cloud.openexperience.content.feature-open-experience-content-standalone-seed.slingosgifeature,/opt/oec/setup/features/cloud.openexperience.example.feature-open-experience-example-seedfar.far"
ENV MAVEN_REPOSITORIES="file:///root/.m2/repository,https://repo.maven.apache.org/maven2,https://repository.apache.org/content/groups/snapshots,https://repository.apache.org/snapshots,https://openexperiencecloud.jfrog.io/artifactory/maven/"

# Copy the customizations
COPY setup/features/ /opt/oec/setup/features/
COPY features/ /opt/oec/features/

# Setup the composite
RUN /bin/bash /opt/oec/setup/setup-composite.sh

# Start Sling CMS
CMD exec java -jar org.apache.sling.feature.launcher.jar \
    -f /opt/oec/features/cloud.openexperience.content.feature-open-experience-content-standalone-runtime.slingosgifeature \
    -f /opt/oec/features/cloud.openexperience.example.feature-open-experience-example-runtimefar.far \
    -u ${MAVEN_REPOSITORIES}