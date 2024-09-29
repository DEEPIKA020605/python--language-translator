import tkinter as tk
from deep_translator import GoogleTranslator

# Define the function to translate the text
def translate_text(text, source_language, target_language):
    try:
        # Perform translation using deep_translator
        if source_language == 'auto':
            # Auto-detect source language
            translated_text = GoogleTranslator(source='auto', target=target_language).translate(text)
        else:
            # Use the selected source language
            translated_text = GoogleTranslator(source=source_language, target=target_language).translate(text)
        return translated_text
    except Exception as e:
        return f"Error: {str(e)}"

# Define the function to handle the button click
def translate_button_click():
    source_text = source_textbox.get('1.0', 'end-1c')  # Get text from source text box
    src_lang = source_language.get()  # Get selected source language
    tgt_lang = target_language.get()  # Get selected target language
    if source_text.strip():  # Check if source text is not empty
        translated_text = translate_text(source_text, src_lang, tgt_lang)  # Perform translation
        target_textbox.delete('1.0', 'end')  # Clear target text box
        target_textbox.insert('1.0', translated_text)  # Insert translated text
    else:
        target_textbox.delete('1.0', 'end')
        target_textbox.insert('1.0', 'Please enter text to translate.')

# Create the GUI window
window = tk.Tk()
window.title('Multi-Language Translator')

# Create the source text box
source_textbox = tk.Text(window, height=10, width=50)
source_textbox.pack(side=tk.LEFT, padx=10, pady=10)

# Create the target text box
target_textbox = tk.Text(window, height=10, width=50)
target_textbox.pack(side=tk.RIGHT, padx=10, pady=10)

# Create the source language dropdown
source_language_label = tk.Label(window, text= 'Source Language (or Auto):')
source_language_label.pack()
source_language = tk.StringVar()
source_language.set('auto')  # Default is auto-detection
source_language_dropdown = tk.OptionMenu(window, source_language, 
                                         'auto', 'en', 'es', 'fr', 'hi', 'de', 'zh-cn', 'ar', 'it', 'ja')
source_language_dropdown.pack()

# Create the target language dropdown
target_language_label = tk.Label(window, text='Target Language:')
target_language_label.pack()
target_language = tk.StringVar()
target_language.set('en')  # Set default language to English ('en')
target_language_dropdown = tk.OptionMenu(window, target_language, 
                                         'en', 'es', 'fr', 'hi', 'de', 'zh-cn', 'ar', 'it', 'ja')
target_language_dropdown.pack()

# Create the translate button
translate_button = tk.Button(window, text='Translate', command=translate_button_click)
translate_button.pack(pady=10)

# Start the GUI event loop
window.mainloop()
