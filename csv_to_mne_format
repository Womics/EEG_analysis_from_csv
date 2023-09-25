#import necessary library
import mne
import pandas as pd
import numpy as np
import scipy.signal as signal
import math

#Read csv data. Our data has unneeded rows, so drop off first 3 rows.
csv_data=pd.read_csv("your_file_name", skiprows=3)

#check the data(if necessary)
#csv_data.head()

# get time and eeg data from csv file
times = csv_data['TIME'].values
eeg_data = csv_data.drop(columns='TIME').values.T

# set some parameters
sfreq = 500  # サンプリングレート (この例では500Hz)
ch_names = list(csv_data.columns[1:])  # 脳波データのカラム名
ch_types = ['eeg'] * len(ch_names)  # すべてのチャンネルをEEGとして設定

# transform into mne data format
info = mne.create_info(ch_names=ch_names, sfreq=sfreq, ch_types=ch_types)
raw = mne.io.RawArray(eeg_data, info)

# plot data
print(raw.info)
raw.plot_psd(fmax=50)
