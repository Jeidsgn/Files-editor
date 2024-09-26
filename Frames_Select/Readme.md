
# Keyframe Selection Tool for EbSynth

This script provides an analytical approach for selecting keyframes to process in **EbSynth**, focusing on detecting frames with the least motion blur. By selecting "static" frames, the tool enhances the quality of the generated results in EbSynth. The number of keyframes and intervals can be manually adjusted based on the length of the video and the desired precision of keyframe selection.

## Motion Blur Analysis

### Mathematical Background

The motion blur analysis involves comparing consecutive frames of a video to calculate the amount of motion or difference between them. The script calculates this difference by computing the **absolute difference** between pixel values in consecutive frames after converting them to grayscale.

Given two grayscale frames, \( F_t \) (current frame) and \( F_{t+1} \) (next frame), the absolute difference is defined as:

\[
\text{difference}(F_t, F_{t+1}) = | F_t - F_{t+1} |
\]

Summing the pixel values in the difference image gives a scalar measure of how much the two frames differ, which serves as a proxy for motion blur:

\[
\text{motion\_blur} = \sum_{i,j} \left( | F_t(i,j) - F_{t+1}(i,j) | \right)
\]

Where \(i,j\) are the pixel coordinates. A lower value indicates that two frames are visually similar, which means the scene is more static, making such frames ideal candidates for keyframes in EbSynth. The keyframes are chosen from intervals of the video by finding the frame with the **lowest motion blur**.

### Steps of the Process:

1. **Video Frame Extraction**: Extracts frames from the input video at a specified frame rate.
2. **Motion Blur Calculation**: Computes motion blur between consecutive frames by calculating their absolute difference.
3. **Interval Division**: Divides the frames into user-defined intervals.
4. **Keyframe Selection**: In each interval, selects the frame with the least motion blur as a keyframe.
5. **Visualization**: Provides a bar chart visualizing the amount of motion blur between frames and highlights the selected keyframes.
6. **Keyframe Saving**: Copies the selected keyframes into a separate folder for further processing in EbSynth.

## Example Workflow

### 1. **Extract Frames**: The script extracts frames from the video and saves them into the "Original" folder. You can adjust the FPS for how frequently frames are extracted.

### 2. **Calculate Motion Blur**: The script compares consecutive frames, calculates the motion blur between them, and stores these values for each frame pair.

### 3. **Select Keyframes**: The frames are divided into intervals, and in each interval, the frame with the least motion blur is selected as a keyframe. The number of intervals can be manually adjusted (`n_intervalos`).

### 4. **Visualize Motion Blur**: A bar chart is generated to visualize the motion blur for each frame. The selected keyframes are annotated on the chart.

### 5. **Save Keyframes**: Finally, the selected keyframes are saved into a "keys" folder, ready to be used in EbSynth.

## Usage

This toolkit is designed to be used in a **Jupyter Notebook** environment for easy customization and execution of individual steps.

### Parameters:
- `ruta_video`: Path to the video file for analysis.
- `fps_deseado`: The desired frame rate for frame extraction.
- `n_intervalos`: Number of intervals to divide the frames for keyframe selection.

### Key Functions:
- `calcular_desenfoque(imagen_previa, imagen_siguiente)`: Computes the motion blur between two consecutive frames.
- `plt.show()`: Visualizes the motion blur across all frames in a bar chart, highlighting the keyframes.

## Example Output:

After running the script, you will get:
- A folder containing extracted frames.
- A bar plot visualizing motion blur across frames.
- A folder with selected keyframes, ready for EbSynth processing.

By adjusting the number of intervals, you can control how many keyframes are selected and their distribution across the video.

## License

This project is open-source and free to use. Modify or distribute as needed.
