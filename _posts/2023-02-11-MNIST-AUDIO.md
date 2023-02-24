# MNIST Audio Classficication

The aim here is to classify sound files into categories. To classify the audio file, details like frequency and frame rate are needed to be represented in an image form, one that looks like the image below. We represent the audio as an image because CNN architectures are well developed to handle images, less so for audio files.
So first lets go through the steps in terms of the theory behind the process and then bring those steps to life using python.

# 1:Theory - Mel spectrogram

![](/images/mel_spec.png "dataset screenshot")

The colour represents intensity, the brighter the more intense the energy (the louder it is). The values at each time interval are derived by applying the fourier transform in order to decompose the sound  into terms of the intensity of its constituent pitches. Then representing that data in terms of the range of frequencies along an x axis of time.




# 1:Practical - Convert audio files to spectograms

In order to convert the audio samples to spectrograms there are a few ingredients needed to make the conversion.

```
def get_wav_info(wav_file):
    wav = wave.open(wav_file, 'r')
    frames = wav.readframes(-1)
    sound_info = pylab.frombuffer(frames, 'int16')
    frame_rate = wav.getframerate()
    wav.close()
    return sound_info, frame_rate



pylab.specgram(sound_info, Fs=frame_rate)
pylab.savefig(f'{file_dist_path}.png')
pylab.close()

```



# 2 Create a CNN

Convolutional Neural Network is an algorithm that takes in an input image, assign weights to areas of pixels in the image, and be able to differentiate the areas from each other. we make a neural network using Conv2D and MaxPooling2D layers to downsample the input images into smaller convolutions, which can be seen as a window of the input image. Combining multiple of these we are able to capture important features in the image such as edges, contours and colors. By iterating over batches of input images and associated labels, we can assign importance via weights to various objects in the image.

```
model = tf.keras.models.Sequential()
model.add(tf.keras.layers.Input(shape=(IMAGE_HEIGHT, IMAGE_WIDTH, N_CHANNELS)))
model.add(tf.keras.layers.Conv2D(32, 3, strides=2, padding='same', activation='relu'))
model.add(tf.keras.layers.BatchNormalization())
model.add(tf.keras.layers.MaxPooling2D(pool_size=(2, 2)))
model.add(tf.keras.layers.BatchNormalization())
model.add(tf.keras.layers.Conv2D(64, 3, padding='same', activation='relu'))
model.add(tf.keras.layers.BatchNormalization())
model.add(tf.keras.layers.MaxPooling2D(pool_size=(2, 2)))
model.add(tf.keras.layers.BatchNormalization())
model.add(tf.keras.layers.Conv2D(128, 3, padding='same', activation='relu'))
model.add(tf.keras.layers.BatchNormalization())
model.add(tf.keras.layers.MaxPooling2D(pool_size=(2, 2)))
model.add(tf.keras.layers.BatchNormalization())
model.add(tf.keras.layers.Flatten())
model.add(tf.keras.layers.Dense(256, activation='relu'))
model.add(tf.keras.layers.BatchNormalization())
model.add(tf.keras.layers.Dropout(0.5))
model.add(tf.keras.layers.Dense(N_CLASSES, activation='softmax'))

# Compile 
model.compile(
    loss='sparse_categorical_crossentropy',
    optimizer=tf.keras.optimizers.RMSprop(),
    metrics=['accuracy'],
)


history = model.fit(train_dataset, epochs=5, validation_data=valid_dataset)
```
# 3 Evaluate

```

final_loss, final_acc = model.evaluate(valid_dataset, verbose=0)
print("Final loss: {0:.6f}, final accuracy: {1:.6f}".format(final_loss, final_acc))
```
