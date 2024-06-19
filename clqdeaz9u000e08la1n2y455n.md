---
title: "Day #15: Python Libraries for DevOps"
seoTitle: "Python Libraries for DevOps"
seoDescription: "Create a Python dictionary mapping cloud service providers to their services and store the data in a JSON file for efficient data handling."
datePublished: Wed Dec 20 2023 06:31:13 GMT+0000 (Coordinated Universal Time)
cuid: clqdeaz9u000e08la1n2y455n
slug: day-15-python-libraries-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Agx5_TLsIf4/upload/58da96d0a16c0ff9d9b96cfdf70cf3aa.jpeg
tags: python, devops

---

In Python, dictionaries are versatile data structures, and often we need to store and exchange data in different formats such as JSON or YAML. In this blog post, we'll explore how to create a dictionary in Python, write it to a JSON file, and read a JSON file containing information about cloud services. Additionally, we'll demonstrate how to read a YAML file and convert its contents to JSON using Python.

## **Task #1 : Creating a Dictionary and Writing to JSON**

```plaintext
# Import the json module
import json

# Create a dictionary with cloud service providers and their services
cloud_services = {
    "aws": "ec2",
    "azure": "VM",
    "gcp": "compute engine"
}

# Specify the file name for the JSON file
json_file_name = "cloud_services.json"

# Write the dictionary to a JSON file
with open(json_file_name, "w") as json_file:
    json.dump(cloud_services, json_file)

print(f"Dictionary written to {json_file_name}")
```

This code creates a dictionary `cloud_services` with cloud service providers and their corresponding services. The `json.dump` function is then used to write this dictionary to a JSON file named `cloud_services.json`.

## **Task #2 : Reading a JSON File**

1. Now, let's read the JSON file (`services.json`) and print the service names of every cloud service provider.
    

```plaintext
# Specify the file name for the JSON file
json_file_name = "services.json"

# Read the contents of the JSON file
with open(json_file_name, "r") as json_file:
    services_data = json.load(json_file)

# Print the service names for each cloud service provider
for provider, service in services_data.items():
    print(f"{provider} : {service}")
```

Assuming the JSON file (`services.json`) has a structure like this:

```plaintext
{
  "aws": "ec2",
  "azure": "VM",
  "gcp": "compute engine"
}
```

This code reads the JSON file and prints the service names for each cloud service provider.

## **Task #3 : Reading YAML and Converting to JSON**

Now, let's read a YAML file (`services.yaml`) and convert its contents to JSON using the PyYAML library.

First, install the PyYAML library if you haven't already:

```plaintext
pip install pyyaml
```

Now, let's proceed with reading the YAML file and converting its contents to JSON.

```plaintext
# Import the yaml module from the PyYAML library
import yaml

# Specify the file name for the YAML file
yaml_file_name = "services.yaml"

# Read the contents of the YAML file
with open(yaml_file_name, "r") as yaml_file:
    yaml_data = yaml.safe_load(yaml_file)

# Convert YAML data to JSON
json_data = json.dumps(yaml_data, indent=2)

# Print the resulting JSON data
print("Converted YAML to JSON:")
print(json_data)
```

This code reads the contents of a YAML file (`services.yaml`) using the PyYAML library and then converts the YAML data to JSON using `json.dumps`. The resulting JSON data is printed to the console.

With these examples, you can work with Python dictionaries, write them to JSON files, read JSON files, and convert YAML to JSON. These skills are useful in various scenarios, especially when dealing with data interchange and configuration files.