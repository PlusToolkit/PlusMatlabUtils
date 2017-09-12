# PlusMatlabUtils
Matlab utilities for reading/writing Plus data structures and communicating with Plus applications

- MatlabMetafileIO: Scripts for reading/writing transforms and images in Matlab, from sequence metafiles (.mha, .mhd) written by Plus
- MatlabOpenIGTLinkInterface: Scripts for real-time receiving of transforms in Matlab through [OpenIGTLink](http://openigtlink.org)

Detailed documentation is available in the headers of the Matlab scripts

# Examples

## Receive live data from trackers from PlusServer

- Download or clone PlusMatlabUtils repository to your computer
- Download and install the Plus package
- Select a configuration file that connects to a tracking device and provides access to the acquired transforms then click Launch Server.
  - "PlusServer: NDI Polaris tracker with passive markers": connect to an NDI Polaris tracker.
  - "PlusServer: Replay...": connect to a simulated tracking device (that reads pre-recorded transforms from a file). No tracking hardware is needed.
- Receive and display transforms by running the `test.m` in scriptMatlabOpenIGTLinkReceiver folder

## Receive live data from 3D Slicer

- Download or clone PlusMatlabUtils repository to your computer
- Download and install 3D Slicer
- Start 3D Slicer
- Go to the Transforms module and create a new LinearTransform (this transform will be sent to Matlab)
- Go to the OpenIGTLinkIF module, create a _new connection_, set it as _Server_, set status to _Active_
- In the I/O configuration tab select Scene/IGTLConnector/OUT
- Click on `+` next to the _Add/remove Node_ selector to add the linear transform to the list of transforms that are broadcasted through OpenIGTLink
- Click on _Push on Connect_ checkbox in the tree for the newly added transform to make sure the transform is sent when Matlab connects (otherwise Slicer only sends the transform whenever is updated)
- In Matlab, run the `testReceiveTransforms.m` script in MatlabOpenIGTLinkInterface folder to receive and display transforms
- Change the LinearTransform in 3D Slicer, the updated transform values will be automatically sent to Matlab

## Send live data to 3D Slicer

- Download or clone PlusMatlabUtils repository to your computer
- Download and install 3D Slicer
- Start 3D Slicer
- Go to the OpenIGTLinkIF module, create a _new connection_, set it as _Server_, set status to _Active_
- In Matlab, run the the `testSendTransform.m` script in MatlabOpenIGTLinkInterface folder receive and display transforms
- The updated transform values will be displayed in the Transforms module in 3D Slicer

# Running Matlab functions from 3D Slicer

MatlabBridge extension in 3D Slicer can be used for running Matlab functions directly from Slicer
(inputs are defined in Slicer and results are visualized immediately in Slicer), see
[MatlabBridge extension documentation](https://www.slicer.org/slicerWiki/index.php/Documentation/Nightly/Extensions/MatlabBridge)
for details.
