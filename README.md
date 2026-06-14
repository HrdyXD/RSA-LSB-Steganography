# RSA-LSB Image Steganography

A Streamlit-based application that combines **RSA encryption** and **Least Significant Bit (LSB) image steganography** to securely hide confidential messages within digital images.

The application provides an end-to-end workflow, including RSA key generation, message encryption, image embedding, message extraction, decryption, and image quality evaluation using MSE and PSNR metrics.

## Features

- Generate RSA 2048-bit public and private keys
- Encrypt plaintext messages using RSA-OAEP
- Hide encrypted messages inside PNG images using LSB steganography
- Support embedding in Red, Green, or Blue channels
- Optional randomized embedding using seed-based positioning
- Extract hidden messages from stego images
- Decrypt extracted ciphertext using RSA private keys
- Visualize ciphertext and pixel modifications
- Evaluate stego image quality using:
  - Mean Squared Error (MSE)
  - Peak Signal-to-Noise Ratio (PSNR)

## Workflow

```text
Plaintext Message
        ↓
RSA Encryption
        ↓
Ciphertext Generation
        ↓
LSB Embedding into Cover Image
        ↓
Stego Image
        ↓
LSB Extraction
        ↓
RSA Decryption
        ↓
Recovered Plaintext
```

## Application Modules

### 1. Generate Key
Generate RSA 2048-bit public and private key pairs for encryption and decryption.

### 2. Encrypt + Steganography
- Input plaintext message
- Upload RSA public key
- Upload PNG cover image
- Select embedding channel (R, G, or B)
- Optional randomized embedding mode
- Generate and download stego image

### 3. Extract + Decrypt
- Upload stego image
- Upload RSA private key
- Extract embedded ciphertext
- Recover the original plaintext message

### 4. MSE and PSNR Evaluation
Analyze the quality difference between cover and stego images using image quality metrics.

## Technologies Used

- Python
- Streamlit
- PyCryptodome
- Pillow (PIL)
- Pandas
- NumPy
- Matplotlib

## Project Structure

```text
RSA-LSB-Steganography/
│
├── app.py
├── README.md
└── requirements.txt
```

## Installation

Clone the repository:

```bash
git clone https://github.com/HrdyXD/RSA-LSB-Steganography.git
cd RSA-LSB-Steganography
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Run the application:

```bash
streamlit run app.py
```

## Image Quality Metrics

### Mean Squared Error (MSE)

Measures the average squared difference between the cover image and the stego image.

```text
MSE = (1/n) × Σ(Cover − Stego)²
```

Lower MSE values indicate smaller image distortion.

### Peak Signal-to-Noise Ratio (PSNR)

Measures the quality of the stego image relative to the original image.

```text
PSNR = 10 × log₁₀(255² / MSE)
```

PSNR interpretation:

| PSNR Value | Quality |
|------------|----------|
| > 40 dB | Excellent |
| 30 – 40 dB | Good |
| 20 – 30 dB | Fair |
| < 20 dB | Poor |

