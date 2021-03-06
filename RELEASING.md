# Releasing

Set variables:

    export VERSION=X.Y.Z
    export GPG_KEY=E7ADD9914E260E8B35DFB50665FDE935573ACDA6
    export BINTRAY_USER=...
    export BINTRAY_KEY=...

Update version numbers:

    vim -p build.gradle README.md CHANGELOG.md

Build:

    ./gradlew build

Add hash to README.md:

    sha256sum build/outputs/aar/saltyrtc-task-webrtc-release.aar

Add and commit:

    git commit -m "Release v${VERSION}"

Publish the library to Bintray:

    ./gradlew bintrayUpload

Tag and push:

    git tag -s -u ${GPG_KEY} v${VERSION} -m "Version ${VERSION}"
    git push && git push --tags

