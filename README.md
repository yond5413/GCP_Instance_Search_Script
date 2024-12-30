# GCP GPU Instance Creator

This script automates the process of creating a Google Cloud Platform (GCP) instance with a GPU attached. It uses the `google-cloud-compute` library to interact with GCP's Compute Engine API and provides a simple command-line interface for configuring and launching the instance.

---

## Features

- **GPU Availability Scanning**: Scans GCP zones to find available GPUs of the specified type.
- **Customizable VM Configuration**: Allows you to specify GPU type, GPU count, machine type, disk size, and more.
- **Automatic Zone Selection**: Automatically selects the first available zone with the required GPU.
- **Progress Tracking**: Uses `tqdm` to display progress bars during zone scanning and VM creation.

---

## Prerequisites

Before using this script, ensure you have the following:

1. **Google Cloud SDK**: Install and configure the Google Cloud SDK on your machine. Follow the [official guide](https://cloud.google.com/sdk/docs/install).
2. **Python Dependencies**: Install the required Python packages using pip:
   ```bash
   pip install fire google-cloud-compute tqdm

GCP Project: Ensure you have a GCP project with billing enabled and the Compute Engine API activated.

#Usage
*Basic Command
To create a VM with default settings, run:
