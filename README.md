# Eigenface
Eigenface with PCA in matlab

# Code
'''
clear all
close all
clc
M = 49; 
for n=1:M
  im = imread(strcat('Dataset/',num2str(n),'.jpg'));
  im=imresize(im,[400 400]);
  im = im2double(rgb2gray(im)); 
  [r,c] = size(im);
  I(n,:) = im(:); 
end
[coeff,score,latent,~,explained,mu] = pca(I);
im = im2double(rgb2gray(imresize(imread('Dataset/33.jpg'),[400 400])));
I_test = im(:);
I_test_weights = zeros(M-1,1);
for jj = 1:M-1
  I_test_weights(jj,1) = dot(I_test,coeff(:,jj));
end
I_recon = coeff*I_test_weights;
I_recon = reshape(I_recon, r,c);
I_recon = mat2gray(I_recon);
figure
subplot(1,2,1);
imshow(im);
title('Original test image');
subplot(1,2,2)
imshow(I_recon);
title('Reconstructed test image');
'''
