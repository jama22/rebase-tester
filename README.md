# Using Google Cloud's Buildpacks with GCB

This project demonstrates how to use a `cloudbuild.yaml`to build an app using[Google Cloud's Buildpacks](https://cloud.google.com/docs/buildpacks/overview). This example will demonstrate how to take advantage of the [`--cache-image` mechanism ](https://buildpacks.io/docs/app-developer-guide/using-cache-image/#using-cache-images---cache-image) to minimise build times.

# How to use
You'll be using the following GCP APIs:
* Cloud Build
* Artifact Registry

You'll also need to have the `gcloud` CLI installed

1. Open `cloudbuild.yaml`
2. Update line 10 with your app image repository name and location
3. Update line 14 with your cache image respository name and location
4. In your terminal, run `gcloud builds submit` 

# How this works
* The provided `cloudbuild.yaml` has a single step that utilizes the `gcr.io/k8s-skaffold/pack` image. This is an image maintained by the Skaffold team and provides the[ Cloud Native Buildpacks `pack` CLI](https://buildpacks.io/docs/tools/pack/)
* We'll be following the instructions on using [`--cache-image` mechanism ](https://buildpacks.io/docs/app-developer-guide/using-cache-image/#using-cache-images---cache-image)to build
   * an app image (line 10)
   * a cache image (line 14)
* First run of this will be relatively slow, generating both the app image and the cache image
* Subsequent runs will take advantage of the cache image to speed up build times