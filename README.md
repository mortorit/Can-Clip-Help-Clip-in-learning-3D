# No Captions, No Problem: Captionless 3D-CLIP Alignment with Hard Negatives via CLIP Knowledge and LLMs

This repository contains the code for the paper "No Captions, No Problem: Captionless 3D-CLIP Alignment with Hard Negatives via CLIP Knowledge and LLMs".

## Installation
Install the required packages using the following command:
```bash
pip install -r requirements.txt
```

Then, install [PointNeXt](https://github.com/user/repo/blob/branch/other_file.md) using the following commands:
```bash
cd models/
git clone --recurse-submodules git@github.com:guochengqian/PointNeXt.git
cd PointNeXt
source update.sh
source install.sh
source update.sh
source install.sh
```
## Data
Download the ShapeNet dataset from the [ULIP 2 repository](https://github.com/salesforce/ULIP/tree/main).

We will release soon the text landmarks embeddings.
Together with that, we will release the code to preprocess the data and create the precomputed similarity matrices.

## Training
To train the model, run the following command:
```bash
python train.py --args
```
The complete list of arguments can be found in the [train.py](train.py) file.

## Evaluation
We release the code for the evaluation of the model on Zero-Shot classification and Cross-Modal retrieval.
Download the datasets and the pretrained model (soon to be released) and run the corresponding scripts:
```bash
python zero_shot_retrieval.py --args
python cross_modal_retrieval.py --args
```
The complete list of arguments can be found in the [test_zeroshot.py](test_zeroshot.py) and [test_retrieval.py](test_retrieval.py) files.

## Models

<table>
    <!-- Title Rows -->
    <tr>
        <th></th>
        <th style="font-size: 16px;"></th>
        <th colspan="4" align="center" style="font-size: 16px;">w/o Background</th>
        <th colspan="4" align="center" style="font-size: 16px;">w/ Background</th>
    </tr>
    <tr>
        <th></th>
        <th style="font-size: 14px;"></th>
        <th colspan="2" align="center" style="font-size: 14px;">Image-to-Shape</th>
        <th colspan="2" align="center" style="font-size: 14px;">Shape-to-Image</th>
        <th colspan="2" align="center" style="font-size: 14px;">Image-to-Shape</th>
        <th colspan="2" align="center" style="font-size: 14px;">Shape-to-Image</th>
    </tr>
    <!-- Header Row -->
    <tr>
        <th>Model</th>
        <th>#P (M)</th>
        <th style="border-left: 1px solid black;">Top-1</th>
        <th>Top-5</th>
        <th>Top-1</th>
        <th>Top-5</th>
        <th style="border-left: 1px solid black;">Top-1</th>
        <th>Top-5</th>
        <th>Top-1</th>
        <th>Top-5</th>
    </tr>
    <!-- Model Rows -->
    <tr>
        <td>PointCLIP</td>
        <td>0</td>
        <td style="border-left: 1px solid black;">13.6</td>
        <td>47.3</td>
        <td>10.1</td>
        <td>42.5</td>
        <td style="border-left: 1px solid black;">9.9</td>
        <td>41.2</td>
        <td>7.4</td>
        <td>34.8</td>
    </tr>
    <tr>
        <td>CLIP2Point</td>
        <td>86</td>
        <td style="border-left: 1px solid black;">20.4</td>
        <td>63.2</td>
        <td>16.5</td>
        <td>53.7</td>
        <td style="border-left: 1px solid black;">15</td>
        <td>50.1</td>
        <td>10.9</td>
        <td>45.2</td>
    </tr>
    <tr>
        <td>ULIP-PointNet++</td>
        <td>1.5</td>
        <td style="border-left: 1px solid black;">23.9</td>
        <td>64.6</td>
        <td>17.2</td>
        <td>55.9</td>
        <td style="border-left: 1px solid black;">15.1</td>
        <td>49.2</td>
        <td>11.4</td>
        <td>47.3</td>
    </tr>
    <tr>
        <td>ULIP-PointBERT</td>
        <td>22.1</td>
        <td style="border-left: 1px solid black;">25.1</td>
        <td>65.8</td>
        <td>17.5</td>
        <td>55.6</td>
        <td style="border-left: 1px solid black;">14.8</td>
        <td>51.4</td>
        <td>12</td>
        <td>47.5</td>
    </tr>
    <tr>
        <td>ReCon</td>
        <td>43.6</td>
        <td style="border-left: 1px solid black;">31.4</td>
        <td>72.8</td>
        <td>22.8</td>
        <td>63.1</td>
        <td style="border-left: 1px solid black;">20.7</td>
        <td>56.4</td>
        <td>19.6</td>
        <td>53.2</td>
    </tr>
    <!-- Double Line Before Our Models -->
   <tr>
        <td colspan="10" style="border-top: 3px double black; font-weight: bold; text-align: center;"></td>
    </tr>
    <!-- "Ours" Models Rows -->
    <tr>
        <td>Ours-I2I</td>
        <td>1.4</td>
        <td style="border-left: 1px solid black;">35.2</td>
        <td>74.4</td>
        <td>27.7</td>
        <td>68.1</td>
        <td style="border-left: 1px solid black;"><strong>26.3</strong></td>
        <td><strong>60.4</strong></td>
        <td>22.8</td>
        <td>56.6</td>
    </tr>
    <tr>
        <td>Ours-(I2L)2</td>
        <td>1.4</td>
        <td style="border-left: 1px solid black;">33.3</td>
        <td>74.4</td>
        <td>26.8</td>
        <td>66.8</td>
        <td style="border-left: 1px solid black;">25.3</td>
        <td>59.9</td>
        <td>22.2</td>
        <td>55.5</td>
    </tr>
    <tr>
        <td><a href="https://polimi365-my.sharepoint.com/:u:/g/personal/10607290_polimi_it/EZQq3xQ8XoNAlTykeBqhsqUBQXFoJA_4TdoQjj9mFLM0lQ?e=bowDu7">Ours-AVG</a></td>
        <td>1.4</td>
        <td style="border-left: 1px solid black;"><strong>35.6</strong></td>
        <td><strong>75.1</strong></td>
        <td><strong>29</strong></td>
        <td><strong>68.7</strong></td>
        <td style="border-left: 1px solid black;">25.9</td>
        <td>60.1</td>
        <td><strong>23.3</strong></td>
        <td><strong>57.8</strong></td>
    </tr>
</table>



