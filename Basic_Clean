### Text cleaning template

## Define stop words
stop_words = set(stopwords.words('english'))
custom_stop_words = ['think', 'know', 're', 'would', 'going', 'they', 'things', 'got',
                     'get', 'want', 'way', 'try', 'lot', 'make', 'see', 'go', 'may',
                     'say', 'something', 'people', 'person', 'really', 'someone', 'come',
                     'came', 'small', 'kind', 'could', 'even', 'like', 'much', 'less',
                     'sense', 'time', 'well', 'consider', 'still', 'give', 'na', 'gon', 'sides', 'situation',
                     'seeing', 'let', 'weeks', 'somebody', 'put', 'one', 'two', 'full',
                     'leave', 'cars', 'generally', 'place', 'compared', 'found', 'background', 'us', 'v']
stop_words = stop_words.union(custom_stop_words)
stop_words = list(stop_words)

## Define contraction mapping dictionary
contractions_mapping = {
    "i'm": "i am",
    "i've": "i have",
    "i'll": "i will",
    "we're": "we are",
    "we've": "we have",
    "we'll": "we will",
    "you're": "you are",
    "you've": "you have",
    "you'll": "you will",
    "he's": "he is",
    "he'll": "he will",
    "she's": "she is",
    "she'll": "she will",
    "it's": "it is",
    "it'll": "it will",
    "they're": "they are",
    "they've": "they have",
    "they'll": "they will",
}

# Function to expand contractions
def expand_contractions(text, contractions_mapping):
    pattern = re.compile(r'\b(' + '|'.join(contractions_mapping.keys()) + r')\b')
    def expand_match(contraction):
        return contractions_mapping[contraction.group(0)]
    expanded_text = pattern.sub(expand_match, text)
    return expanded_text

## Function to remove proper nouns
def remove_proper_nouns(tokens):
    tagged = pos_tag(tokens)
    return [word for word, tag in tagged if tag != 'NNP' and tag != 'NNPS']

## Main function to clean and preprocess text
def clean_text(text):
    # Remove non-alphabetic characters
    text = re.sub('[^A-Za-z]', ' ', text)
    # Expand contractions
    text = expand_contractions(text, contractions_mapping)
    # Tokenize the text
    tokens = word_tokenize(text)
    # Remove proper nouns
    tokens = remove_proper_nouns(tokens)
    # Convert to lowercase
    tokens = [word.lower() for word in tokens]
    # Remove stopwords
    cleaned_text = ' '.join([word for word in tokens if word not in stop_words])
    return cleaned_text

## Apply cleaning to column: columname
#dfCLEAN['columnameCLEAN'] = df['columname'].apply(clean_text)
