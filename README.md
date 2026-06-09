# **3D Vector Transformation API**

## **IMPORTANT NOTE FOR FINAL SUBMISSION**
For those reviewing this repository for final submission, I have added a file called "FINAL-PROJECT-SUBMISSION" in the DOCUMENTS folder. The purpose of this folder is to gather all the necessary CI/CD artifacts I have created in the past into a single folder for ease of review. All original documents still can be found manually by navigating within the repository. 

This folder includes the following CI/CD artifacts: 
1. Test Strategy Document
2. Test Plan Document
3. Manual Test Suite (and reasoning)
4. Test Report (Automated + Manual)
5. CI troubleshooting/maintenance reflection (designing testable software)

This folder also includes a README file that details guidance to find the following CI/CD artifacts: 
1. Automated Unit Tests
2. Automated Integration Tests
3. Automated E2E Tests
4. Basic CI workflow in GitHub Actions that run automated tests

## Updates
# This file includes all updates about the mock project.

## 6/6/2026 Updates
Updated workflow to test project with compiler GCC and Clang. 

## 5/31/2026 Updates

Moved documents to "DOCUMENTS" file. The DOCUMENT file includes subfiles that organize documents. 

Added Specialized Tests in test.cpp

Added Dockerfile.gcc for manual compatibility testing (For manual testing instruction, refer to below.)

Added Dockerfile.clang for manual compatibility testing (For manual testing instruction, refer to below.)

Added DOC-COMMON-ISSUE in DOCUMENTS/ASSIGNMENT-5 folder. This file includes information about common issues associated with my product. 

Added DOC-CONFIGURATION in DOCUMENTS/ASSIGNMENT-5 folder. This file includes information about configuration that should be tested before production. 

Added DOC-SPECIALIZED-TESTING in DOCUMENTS/ASSIGNMENT-5 folder. This file includes information about automated specialized testing used to validate the product. The implementation is found in LA-TEST-ENV/test.cpp.

Added REPORT-SPECIALIZED-MANUAL-SPECIALIZED-TEST in DOCUMENTS/ASSIGNMENT-5 folder. This file includes information about manual testing done for the product. 

---
### 5/17/2026 Updates
Added PRODUCT-QUESTIONNAIRE-ORIGINAL. Original copy of questionnaire to be given to test after tests.

Added PRODUCT-QUESTIONNAIRE-SAMPLE-SUBMISSION. Filled out copy of the questionnaire. It is stated sample but, this will be feedback to the current state of the project.

Added DOCUMENTATION-E2E-MANUAL-TEST. 

Added TEST-REPORT(E2E-TEST). 

Added ANALYSIS-BEST-SCENARIO. Analysis of scenario used in the automated E2E test.

Added automated E2E section to test.cpp. 

---
### 5/3/2026 Updates 

Added a YAML file to enable GitHub Actions.

Added rotateEulerX function. The purpose of adding this is to test sequential rotation.

Added rotateEulerY function. The purpose of adding this is to test sequential rotation.

Modified quatFromAxisAngle function to handle normalization internally.

---
## Purpose
It's purpose is to provide developers an easy tool to transform 3D vector. 

---
## READ THIS BEFORE USAGE!
When using this API, it is necessary to keep in mind the orientations of each axis.

| Axis | Direction |
|------|-----------|
| +z | Up |
| -z | Down |
| +x | Right |
| -x | Left |
| +y | Inward |
| -y | Outward |

If the API is used in any other coordinate system, there will be unexpected results.

---
## Features

| Name | Explanation |
|------|-------------|
| Vec3 | A struct that stores information in order of x, y, z. Intended for Cartesian coordinates. |
| Vec3.operator+ | Operator override to ease vector calculation. Must match dimension for proper calculation. |
| Vec3.operator- | Operator override to ease vector calculation. Must match dimension for proper calculation. |
| Vec3.operator* | Operator override to ease vector calculation. Must match dimension for proper calculation. |
| Vec3.operator/ | Operator override to ease vector calculation. Must match dimension for proper calculation. |
| Vec4 | A struct that stores information in order of x, y, z, w. Intended for homogeneous coordinates. |
| Vec4.operator+ | Operator override to ease vector calculation. Must match dimension for proper calculation. |
| Vec4.operator- | Operator override to ease vector calculation. Must match dimension for proper calculation. |
| Vec4.operator* | Operator override to ease vector calculation. Must match dimension for proper calculation. |
| Vec4.operator/ | Operator override to ease vector calculation. Must match dimension for proper calculation. |
| Quat | A struct that stores information in order of x, y, z, w. Intended for storing Quaternion. |
| dot3 | This function takes Vec3 objects and returns the dot product of the two vectors. |
| cross3 | This function takes Vec3 objects and returns new Vec3 that is perpendicular to input vectors. |
| rotateEulerX | This function takes in a single Vec3 object and a degree angle to rotate about x axis. |
| rotateEulerY | This function takes in a single Vec3 object and a degree angle to rotate about y axis. |
| rotateEulerZ | This function takes in a single Vec3 object and a degree angle to rotate about z axis. |
| magnitude | This function takes in a single Vec3 and returns the magnitude of the vector. |
| quatFromAxisAngle | This function takes a Vec3 vector object and angle of degree to return a corresponding quaternion. |
| normalizeQuat | This function take in a Quat object and returns normalized quaternion. |
| quatMultiply | This function takes two Quat object and returns the muliplied quaternion. |
| quatRotate | This function takes Quat object (used for rotation) and Vec3 object (intended to be rotated) to rotate Vec3. |

---
## Test Yourself!

### Prerequisite:
Docker Desktop

### Steps:

1. Clone the repository to a desired location.
2. Open a command line interface and navigate to src folder. This folder includes the Dockerfile.
3. Build the Dockerfile using the following command: docker build -t "Your Image Name Goes Here"
4. Once the image is created, run the application using this command: docker run "You Image Name Goes Here"

### Here's how it should look on your cli (I've used "test" for my images name):
```bash
docker build -t test .
docker run test
```

### Here's how it should look if you are manually testing gcc (I've used "cpp-gcc-test" for my image name):
```bash
docker build -f Dockerfile.gcc -t cpp-gcc-test .
docker docker run cpp-gcc-test
```
### Here's how it should look if you are manually testing clang (I've used "cpp-clang-test" for my image name):
```bash
docker build -f Dockerfile.gcc -t cpp-clang-test .
docker docker run cpp-clang-test
```

## Common Error During Manual Testing

When manual testing, be sure that you have opened the Docker Desktop software before step 2 or you will get an error message. 
(On Windows Platform)
```bash
css508-LinearAlgebraLibrary\LA-TEST-ENV>docker build -t test .
ERROR: failed to connect to the docker API at npipe:////./pipe/dockerDesktopLinuxEngine; check if the path is correct and if the daemon is running: open //./pipe/dockerDesktopLinuxEngine: The system cannot find the file specified.

```