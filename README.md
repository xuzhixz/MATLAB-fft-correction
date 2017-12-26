# MATLAB-fft-correction
matlab快速傅里叶变换所得结果需要进行修正

function [A,w] = myfft(y,fs)
%时域信号y，采样频率fs,输入格式[A,w] = myfft(y,fs)

N=2^nextpow2(length(y));%找出大于y的个数的最大的2的指数值（自动进算最佳FFT步长nfft）
y=y-mean(y);%去除直流分量
fft1=fft(y,N);%对y信号进行DFT，得到频率的幅值分布
w=fs*(0:N/2-1)/N;频率修正
A =abs(fft1(1:N/2))*2/N;幅值修正
end
