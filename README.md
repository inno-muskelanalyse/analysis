# Readme

This program takes a segmented image of a muscle strand as input and returns key parameters such as length, width, orientation, and midpoint.

## Requirements

- Python
- imutils
- scipy
- opencv-python
- numpy

The requirements can be installed from the command line using the following syntax:

```bash
pip install -r requirements.txt
```

## Usage

The program can be called from the command line using the following syntax:

```bash
python main.py <path-to-segmented-image>
python main.py <path-to-segmented-image> <path-to-segmented-image> <path-to-segmented-image>
```

It can be called with just one or multiple paths.

Alternatively, you can use the following command to run the program in "development" mode, which will display the output to the console:

```bash
python main.py -d path <path-to-segmented-image>
python main.py -d path <path-to-segmented-image> <path-to-segmented-image> <path-to-segmented-image>
```

## Output

The program returns a JSON object with two possible values for the "status" key: "ok" or "error".

### OK

If the program runs successfully and is able to detect the muscle strand, the output will be in the following format:

```JSON
{
  "status": "ok",
  "data": [
      {
      "path": "<path-to-segmented-image>",
      "directionA": <directionA-value>,
      "directionB": <directionB-value>,
      "angle": <angle-value>,
      "midpointX": <midpointX-value>,
      "midpointY": <midpointY-value>,
      "status": "success"
    }
  ]
}
```

Or for multiple images:

```JSON
{
  "status": "ok",
  "data": [
    {
      "path": "<path-to-segmented-image>",
      "directionA": <directionA-value>,
      "directionB": <directionB-value>,
      "angle": <angle-value>,
      "midpointX": <midpointX-value>,
      "midpointY": <midpointY-value>,
      "status": "success"
    },
    {
      "path": "<path-to-segmented-image>",
      "directionA": <directionA-value>,
      "directionB": <directionB-value>,
      "angle": <angle-value>,
      "midpointX": <midpointX-value>,
      "midpointY": <midpointY-value>,
      "status": "success"
    }
  ]
}
```

The values for "directionA", "directionB", "angle", "midpointX", and "midpointY" will be numeric values representing the detected parameters for the muscle strand.

If the program runs successfully, but is unable to detect the muscle strand, the output will be in the following format:

```JSON
{
  "status": "ok",
  "data": [{
    "path": "<path-to-segmented-image>",
    "directionA": <directionA-value>,
    "directionB": <directionB-value>,
    "angle": <angle-value>,
    "midpointX": <midpointX-value>,
    "midpointY": <midpointY-value>,
    "status": "error"
  }]
}
```

In this case, the "status" key in the main JSON object will be "ok", but the "status" key in the "data" sub-object will be "error".

### Error

If the program encounters an error, the output will be in the following format:

```JSON
{
  "status": "error",
  "message": "<error-message>",
  "error": "<error>"
}
```

The "message" key will contain a human-readable error message, and the "error" key will contain the corresponding error code.
