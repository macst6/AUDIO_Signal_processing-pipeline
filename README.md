# AUDIO_Signal_processing-pipeline
This repositiry contains the code of audio Pipeline 
#Preprocessing Pipeline

# 1-Load the file
---------------
---------------


#Constructor  
--------------------
#We are passing a constructor in the loader Class that will construct the class
#It has following arguments 
# Sample rate -> we load audio file with this
# Duration -> How long audio will play (sec)
# Mono -> it is boolean and tells us if audio is mono or stereo




# Load 
------------
#Then we added a load class that will load our signal with the parameters of the constructor and it will give us the constructed signal
#This will return us the signal with sample rate , Duration and will tell if the signal is mono oe stereo







#Pad the signal if necessay
-----------------------------
-----------------------------
Padder is the Function to padding the data in array


#Constructor Class 
--------------------
Here we have mode



#This function is for left Padding 
------------------------------------
#Here we pass the array and number of missing items
#[1,2,3] -> Left padding of 2 -> [0,0,1,2,3]
#Pad using the numpy array
#Array | number of missing items -> 0 



#This function is for right Padding
-----------------------------------
#Here we pass the array and number of missing items
#[1,2,3] -> Right padding of 2 -> [1,2,3,0,0]
#Array |  0 -> number of missing items


#Extracting log spectogram using Librosa
----------------------------------------
----------------------------------------

#LogSpectogramExtractor creates a log spectogram in dB from a time series Signal

#Constructor Class 
--------------------
#Here we have following parameters
#Frame Size 
#Hop Length

#Extractor 
--------------------

#(1+frame_size/2,num_frame)  1024 -> 513 -> 512
#We take the signal then we use framesize and we decide the hoplength we want 







#Normalize Spectogram
----------------------
----------------------
#MinMax Normalization applies min max normalization to array


#Constructor Class 
--------------------
# min_value -> We take a minimum value that is mapped close to zero
# max_value -> We take a maximum value that is mapped close to one

#Normalize Class 
--------------------
#array will be squished between 0 and 1
#1st step to Normalize array -> (array-array.min())/(array.max()-array.min())
#2nd step to Normalize array -> Normalize array + (self.max - self.min)




#Denormalize Class
--------------------
#array will be squished between 0 and 1
#1st step to Normalize array -> (norm_array-self.min)/(self.max()-self.min())
#2nd step to Normalize array -> array * (original_max - original_min) + original_min






#Save the Normalized Spectogram
--------------------------------
--------------------------------


#Saver Class
--------------------
#saver is responsible to save features, and the min max values

#Constructor Class 
--------------------
#We need feature save directory and min max value directory as the constructors that make the saver

#save_feature Class 
--------------------
#We generated save path and generated the path
#save the path of the feature


#save_min_max_values Class 
----------------------------
#We generated save path and generated the path
#save the path of the feature


#save_min_max_values Class 
----------------------------
save_min_max_values








#PreprocessingPipeline processes audio files in a directory, applying the following steps to each file:
        # 1- load a file
        # 2- pad the signal (if necessary)
        # 3- extracting log spectrogram from signal
        # 4- normalise spectrogram
        # 5- save the normalised spectrogram
-----------------------------------------------------
------------------------------------------------------


#process Class 
----------------------------
#looping through filepath which is the directory containing all the file
#We are going through all the directories and subdirectories
#Now we are reconstructing the filepath root directory + file 


#_process_file Method 
----------------------------
#it is the bulk of the class
#We will load the signal
#Now we are deciding wether we want to apply padding or not
#Then we are moving to is padding necessary function
#if the signal need padding then we will apply that to the signal
#Now we are extracting the feature
#Then we will save the normalized feature
#Then we will save the path




#_is_padding_necessary Method 
----------------------------
#How are we gonna check if the signal needs padding or not 
#Duration is fixed and we know number of expected samples
#So if the length of the signal is less than expected samples then we provide results as boolean value

#_apply_padding Method 
----------------------------
#Here we will give the signal
#Number of missing samples = Number of expected samples - length of signal


#_store_min_max_value Method 
----------------------------
#This will store the dictionary of minimum and maximum value
