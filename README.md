# Speech-Enhancement-Project
methods = {'Noisy','C-Net'};
pesq = [1.40 2.24];

bar(pesq)
set(gca,'XTickLabel',methods)
ylabel('PESQ')
title('PESQ Comparison')
grid on

methods = {'Noisy','C-Net'};
stoi = [0.89 0.90];

bar(stoi)
set(gca,'XTickLabel',methods)
ylabel('STOI')
title('STOI Comparison')
grid on

import librosa
import librosa.display
import matplotlib.pyplot as plt
import numpy as np

y,sr = librosa.load("speech.wav",sr=16000)

D = librosa.stft(y)

plt.figure(figsize=(10,4))
librosa.display.specshow(
    librosa.amplitude_to_db(np.abs(D)),
    sr=sr,
    x_axis='time',
    y_axis='log',
    cmap='viridis'
)
plt.colorbar()
plt.show()


methods = {'Noisy','C-Net'};
pesq = [1.40 2.24];

bar(pesq)
set(gca,'XTickLabel',methods)
ylabel('PESQ')
title('PESQ Comparison')
grid on

[x,fs] = audioread('speech.wav');

[S,F,T] = spectrogram(x,512,256,512,fs);

imagesc(T,F,20*log10(abs(S)));
axis xy;
colormap(parula);
colorbar;
title('Colored Spectrogram');
maps = {'parula','jet','turbo','hsv','hot','cool','spring','summer'};

for i = 1:length(maps)
    subplot(2,4,i)
    imagesc(peaks(100))
    colormap(gca,maps{i})
    title(maps{i})
    axis off
end
