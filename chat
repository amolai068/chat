

# import streamlit as st
# import base64
# import time
# from PIL import Image
# from io import BytesIO

# # Simple XOR Encryption/Decryption with Base64 Encoding
# def xor_encrypt_decrypt(message, key):
#     return ''.join(chr(ord(c) ^ ord(k)) for c, k in zip(message, key * ((len(message) // len(key)) + 1)))

# def encode_message(message, key):
#     encrypted = xor_encrypt_decrypt(message, key)
#     return base64.b64encode(encrypted.encode()).decode()

# def decode_message(encoded_message, key):
#     encrypted = base64.b64decode(encoded_message).decode()
#     return xor_encrypt_decrypt(encrypted, key)

# # Simulate persistent storage for messages and images
# if 'messages' not in st.session_state:
#     st.session_state['messages'] = []
# if 'images' not in st.session_state:
#     st.session_state['images'] = []

# # Encryption key
# KEY = "simplekey"

# # Sidebar for User Selection
# user = st.sidebar.selectbox("Select User", ["User 1", "User 2"])
# other_user = "User 2" if user == "User 1" else "User 1"
# st.sidebar.write(f"You are chatting with: {other_user}")

# # Display chat history
# def display_messages():
#     for msg in st.session_state['messages']:
#         sender, encoded_msg = msg
#         decrypted_msg = decode_message(encoded_msg, KEY)
#         if sender == user:
#             st.write(f"**You:** {decrypted_msg}")
#         else:
#             st.write(f"**{other_user}:** {decrypted_msg}")

#     for img in st.session_state['images']:
#         sender, image_data = img
#         image = Image.open(BytesIO(image_data))  # Convert binary to image
#         if sender == user:
#             st.image(image, caption="You:", use_column_width=True)
#         else:
#             st.image(image, caption=f"{other_user}:", use_column_width=True)

# # Input box for new messages and image upload
# st.title("Messaging App with Image Upload")

# # Message form
# with st.form(key="message_form"):
#     new_message = st.text_input("Type your message:", key=f"input-{user}")
#     submitted = st.form_submit_button("Send")

# # Add the new message to chat history
# if submitted and new_message:
#     encoded_message = encode_message(new_message, KEY)
#     st.session_state['messages'].append((user, encoded_message))

# # Image uploader below the form
# uploaded_image = st.file_uploader("Upload an image:", type=["png", "jpg", "jpeg"], key=f"upload-{user}")
# if uploaded_image:
#     # Read the binary content of the image
#     image_data = uploaded_image.read()
#     st.session_state['images'].append((user, image_data))
#     st.success(f"Image uploaded successfully by {user}!")

# # Clear chat functionality
# if st.button("Clear Chat"):
#     st.session_state['messages'] = []
#     st.session_state['images'] = []
#     st.success("Chat history cleared!")

# # Display chat history
# st.subheader("Chat History")
# display_messages()



# # Placeholder for audio and video calls
# st.subheader("Audio and Video Call")
# if st.button("Start Audio Call"):
#     st.info("Audio call feature coming soon! Use a third-party service like Twilio or WebRTC.")
# if st.button("Start Video Call"):
#     st.info("Video call feature coming soon! Use a third-party service like Twilio or WebRTC.")


import streamlit as st
import base64
from PIL import Image
from io import BytesIO

# Simple XOR Encryption/Decryption with Base64 Encoding
def xor_encrypt_decrypt(message, key):
    return ''.join(chr(ord(c) ^ ord(k)) for c, k in zip(message, key * ((len(message) // len(key)) + 1)))

def encode_message(message, key):
    encrypted = xor_encrypt_decrypt(message, key)
    return base64.b64encode(encrypted.encode()).decode()

def decode_message(encoded_message, key):
    encrypted = base64.b64decode(encoded_message).decode()
    return xor_encrypt_decrypt(encrypted, key)

# Simulate persistent storage for messages and images
if 'messages' not in st.session_state:
    st.session_state['messages'] = []
if 'images' not in st.session_state:
    st.session_state['images'] = []

# Encryption key
KEY = "simplekey"

# Custom CSS for background and chat styling
page_bg_img = '''
<style>
body {
    background-image: url("https://www.transparenttextures.com/patterns/white-wall.png");
    background-size: cover;
    font-family: 'Arial', sans-serif;
}

.chat-bubble {
    padding: 10px 15px;
    margin: 10px 0;
    border-radius: 20px;
    display: inline-block;
    max-width: 70%;
    word-wrap: break-word;
}

.user-bubble {
    background-color: #4CAF50; /* Green Bubble */
    color: white;
    align-self: flex-end;
    margin-left: auto;
}

.other-user-bubble {
    background-color: #E5E5EA; /* Gray Bubble */
    color: black;
    align-self: flex-start;
}

.chat-container {
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 10px;
    background-color: rgba(255, 255, 255, 0.7);
    max-height: 400px;
    overflow-y: auto;
}

.upload-container {
    margin-top: 10px;
}

button {
    background-color: #4CAF50;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #45a049;
}

h1, h2, h3 {
    color: #4CAF50;
    text-align: center;
}
</style>
'''
st.markdown(page_bg_img, unsafe_allow_html=True)

# Sidebar for User Selection
user = st.sidebar.selectbox("Select User", ["User 1", "User 2"])
other_user = "User 2" if user == "User 1" else "User 1"
st.sidebar.write(f"You are chatting with: {other_user}")

# Display chat history
st.title("Telegram/WhatsApp Styled Chat")

def display_messages():
    st.markdown('<div class="chat-container">', unsafe_allow_html=True)
    for msg in st.session_state['messages']:
        sender, encoded_msg = msg
        decrypted_msg = decode_message(encoded_msg, KEY)
        if sender == user:
            st.markdown(f'<div class="chat-bubble user-bubble">{decrypted_msg}</div>', unsafe_allow_html=True)
        else:
            st.markdown(f'<div class="chat-bubble other-user-bubble">{decrypted_msg}</div>', unsafe_allow_html=True)
    for img in st.session_state['images']:
        sender, image_data = img
        image = Image.open(BytesIO(image_data))  # Convert binary to image
        if sender == user:
            st.image(image, caption="You:", use_column_width=True)
        else:
            st.image(image, caption=f"{other_user}:", use_column_width=True)
    st.markdown('</div>', unsafe_allow_html=True)

# Layout with chat history on top
st.subheader("Chat History")
display_messages()

# Input box for new messages and image upload at the bottom
st.subheader("Send a Message")

# Message form
with st.form(key="message_form"):
    new_message = st.text_input("Type your message:", key=f"input-{user}")
    uploaded_image = st.file_uploader("Upload an image:", type=["png", "jpg", "jpeg"], key=f"upload-{user}")
    submitted = st.form_submit_button("Send")

# Add the new message to chat history
if submitted:
    if new_message:
        encoded_message = encode_message(new_message, KEY)
        st.session_state['messages'].append((user, encoded_message))
    if uploaded_image:
        # Read the binary content of the image
        image_data = uploaded_image.read()
        st.session_state['images'].append((user, image_data))
        st.success("Image uploaded successfully!")

# Clear chat functionality
if st.button("Clear Chat"):
    st.session_state['messages'] = []
    st.session_state['images'] = []
    st.success("Chat history cleared!")
