# Kinect Data

Collection of skeleton and point cloud data using Kinect V2 - in **JSON** for 3D environments on the web.

## Data Format

The whole of each data set is in an array. Each element of the outer-most array contains data from a single kinect.
In each array element containing data from a single connect, each element contains an object of data of each body detected by the kinect machine.

```javascript
[[{body1}, {body2} ... ], [{body1}, {body2} ... ] ... ]
```

Each of the body objects contain 5 elements: bodyIndex, joints, leftHandState, rightHandState and trackingId.

* bodyIndex is given in an ascending for each body detected by the Kinect machine.
* joints is an array that contains 20 objects (one for each of the 20 joints - in order. For specific order of the joints please review section on [Joint Index](#joint-index) ). Each object contains 4 elements:
  * px: an array that contains point cloud x, y, and z positions around the joint
  * x: x coordinate of the joint
  * y: y coordinate of the joint
  * z: z coordinate of the joint
* leftHandState: 0 (open) || 1 (closed)
* rightHandState: 0 (open) || 1 (closed)
* trackingId: unique tracking ID for the skeleton

```javascript
[[{
  "bodyIndex" : 0,
  "joints": [
    {
      px: [
        {"x": 298,
         "y": 208,
         "z": 110},
        {"x": 274,
         "y": 236,
         "z": 133}, 
         ...
      ],
      "x": 296,
      "y": 214,
      "z": 117
    }
    ...
  ],
  "leftHandState": 1,
  "rightHandState": 0,
  "trackingId": "72057594037930055"
  }, {body2} ... ], [{body1}, {body2} ... ] ... ]
```
## Joint Index

0. SPINE BASE
1. SPIN MID
2. NECK
3. HEAD
4. SHOULDER LEFT
5. ELBOW LEFT
6. WRIST LEFT
7. HAND LEFT
8. SHOULDER RIGHT
9. ELBOW RIGHT
10. WRIST RIGHT
11. HAND RIGHT
12. HIP LEFT
13. KNEE LEFT
14. ANKLE LEFT
15. FOOT LEFT
16. HIP RIGHT
17. KNEE RIGHT
18. ANKLE RIGHT
19. FOOT RIGHT

*There are for more joints that are usually detected by Kinect, which are omitted in this data set, which are: SPIN SHOULDER (20), HAND TIP LEFT (21), THUMB RIGHT (22), HAND TIP RIGHT (23), THUMB RIGHT (24). These joints were chosen to be omitted from collecting point cloud data due to too much overlap with point cloud collected from other "bigger" joints.

## Catagories of Data Sets

Most of JSON files exist in two versions: FULL and MIN.
* FULL files are "prettier" JSON files - those that have indentation and new line characters. Bigger in size, but easy to look at to study the data itself.
* MIN files contain no whitespaces. More light-weight and easier to use in code.

There are three folders in this dataset: 
* 1-person: Each of the recorded JSON file contains action(s) of one person.
* 2-person: Each of the recorded JSON file contains action(s) of two people.
* 3-person: Each of the recorded JSON file contains action(s) of three people.

## Data Collection

All data in this data set is recorded using the JSON recording feature of [The Flow Room](https://github.com/js6450/theFlowRoom), a project *STILL IN DEVELOPMENT*. The Flow Room server-side framework was built using Kinect V2 Node Module.
