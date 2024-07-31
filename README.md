# Streamlit App with Google Colab

## Overview

This project demonstrates how to launch a Streamlit app from Google Colab using a subprocess and threading. The app displays a simple message using Streamlit, and the setup includes creating a tunnel to access the app remotely via `serveo.net`.

## Prerequisites

1. **Google Colab**: This code is intended to run within a Google Colab notebook.
2. **Streamlit**: Ensure that Streamlit is installed in your Colab environment.
3. **Serveo**: Used to create a tunnel for remote access to the Streamlit app.

## Installation

1. **Install Streamlit**: Run the following command in a Colab cell to install Streamlit:

    ```python
    !pip install streamlit
    ```

2. **Create the Streamlit App File**: Use the following code to create the `app.py` file in your Colab environment:

    ```python
    %%writefile app.py
    import streamlit as st

    st.title('Hello, AI Community! I am Abbas Khan the datascientist')

    st.title('This is the Test to launch a Streamlit App from Google Colab.')
    ```

3. **Run the Streamlit App**: The following code runs the Streamlit app using a subprocess and creates a tunnel for remote access:

    ```python
    import subprocess
    import threading

    # Function to run the Streamlit app
    def run_streamlit():
        subprocess.run(["streamlit", "run", "app.py"])

    # Run Streamlit app in a separate thread
    thread = threading.Thread(target=run_streamlit)
    thread.start()
    # Create a tunnel using serveo.net
    !ssh -o StrictHostKeyChecking=no -R 80:localhost:8501 serveo.net
    ```

## Usage

1. **Start the Colab Cell**: Execute the cell that creates and runs the Streamlit app. This will start the app and create a tunnel.
2. **Access the App**: Once the tunnel is created, you will receive a URL from `serveo.net` where you can access your Streamlit app.

## Notes

- **Serveo.net**: This service is used to expose the localhost to the public internet. Ensure that you follow security best practices when using such services.
- **Threading**: The use of threading allows the Streamlit app to run asynchronously from the notebook cell.

## Troubleshooting

- **Streamlit Not Running**: Check the Colab output for any errors in the subprocess or Streamlit installation.
- **Tunnel Issues**: If the tunnel does not work, try restarting the cell or using an alternative tunneling service.


