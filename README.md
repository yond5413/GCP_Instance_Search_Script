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

## Usage
*Basic Command*
To create a VM with default settings, run:
```
python3 create_gcp_instance.py --project_id="your-project-id" --vm_name="your-vm-name"
```

## Custom Configuration
You can customize the VM configuration using additional parameters:
```
python3 create_gcp_instance.py \
  --project_id="your-project-id" \
  --vm_name="your-vm-name" \
  --gpu_type="nvidia-tesla-v100" \
  --gpu_count=2 \
  --machine_type="n1-standard-16" \
  --disk_size=200
```
```
Parameters
 Parameter            |	Description                                                         |	Default Value
--project_id          |	Your GCP project ID.	                                               |  Required
--vm_name	          |The name of the VM instance.	                                      |  Required
--gpu_type	          |The type of GPU to attach (e.g., nvidia-tesla-t4, nvidia-l4).	     | "nvidia-tesla-t4"
--gpu_count	          |The number of GPUs to attach.	                                      |    4
--machine_type        |	The machine type for the VM (e.g., n1-standard-8, g2-standard-8).   | 	"n1-standard-8"
--disk_source_image   |	The source image for the boot disk.                                 |	"projects/ml-images/global/images/c0-deeplearning-common-cu121-v20240306-debian-11"
--disk_size           |	The size of the boot disk in GB.	                                   |   100
--num_zones_to_check  |	The number of zones to check for GPU availability.	                 |   200
```
Example
To create a VM with the following configuration:

Project ID: high-performance-ml

VM Name: my-lil-vm

GPU Type: nvidia-tesla-t4

GPU Count: 4

Machine Type: n1-standard-8

Disk Size: 100 GB

Run the command:

python3 create_gcp_instance.py \
  --project_id="high-performance-ml" \
  --vm_name="my-lil-vm" \
  --gpu_type="nvidia-tesla-t4" \
  --gpu_count=4 \
  --machine_type="n1-standard-8" \
  --disk_size=100
How It Works
Scan Zones: The script scans GCP zones to find available GPUs of the specified type.

Create VM: It creates a VM in the first available zone with the required GPU.

Configure VM: The VM is configured with the specified GPU, machine type, disk size, and other settings.

Handle Errors: If VM creation fails in one zone, the script attempts to create the VM in the next available zone.

Notes
Default Network: The script uses the default network and subnetwork for the VM.

Host Maintenance: The VM will be terminated if the host undergoes maintenance.

Progress Bars: The script uses tqdm to display progress bars during zone scanning and VM creation.




