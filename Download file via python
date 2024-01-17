
import requests
from tqdm import tqdm

def download_file(url, filename):
    response = requests.get(url, stream=True)

    # Get the total file size
    total_size = int(response.headers.get('content-length', 0))

    # Initialize a progress bar
    progress_bar = tqdm(total=total_size, unit='iB', unit_scale=True)

    with open(filename, 'wb') as file:
        for data in response.iter_content(chunk_size=1024):
            # Write data read to the file
            file.write(data)
            
            # Update the progress bar
            progress_bar.update(len(data))

    progress_bar.close()

    if total_size != 0 and progress_bar.n != total_size:
        print("ERROR, something went wrong")

# The URL of the file you want to download
url = 'https://prod-dcd-datasets-cache-zipfiles.s3.eu-west-1.amazonaws.com/ydrm75xywg-1.zip'

# The path where you want to save the file
filename = '/content/drive/MyDrive/CASD_Dataset/downloaded_file.zip'

download_file(url, filename)
