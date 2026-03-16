import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

fs = 500
t = np.linspace(0,1,fs)

signal_input = np.sin(2*np.pi*5*t) + 0.5*np.sin(2*np.pi*40*t)
noise = 0.5*np.random.randn(fs)
signal_noisy = signal_input + noise

b,a = signal.butter(4,0.1,'low')
low = signal.filtfilt(b,a,signal_noisy)

b,a = signal.butter(4,0.3,'high')
high = signal.filtfilt(b,a,signal_noisy)

b,a = signal.butter(4,[0.2,0.4],'band')
band = signal.filtfilt(b,a,signal_noisy)
