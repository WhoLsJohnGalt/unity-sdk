# Language Translation

[Language Translation][language_Translation] translates text from one language to another. The service offers multiple domain-specific models that you can customize based on your unique terminology and language. Use Language Translation to take news from across the globe and present it in your language, communicate with your customers in their own language, and more.

## Usage
Select a domain, then identify or select the language of text, and then translate the text from one supported language to another.

### Instantiating and authenticating the service
Before you can send requests to the service it must be instantiated and credentials must be set.
```cs
using IBM.Watson.DeveloperCloud.Services.LanguageTranslation.v2;
using IBM.Watson.DeveloperCloud.Utilities;

void Start()
{
    Credentials credentials = new Credentials(<username>, <password>, <url>);
    LanguageTranslation _languageTranslation = new LanguageTranslation(credentials);
}
```





### List models
Lists available models for language translation with option to filter by source or by target language.
```cs
private void GetModels()
{
  if (!_languageTranslation.GetModels(OnGetModels))
    Log.Debug("ExampleLanguageTranslation.GetModels()", "Failed to get models.");
}

private void OnGetModels(TranslationModels models, string data)
{
  Log.Debug("ExampleLanguageTranslation.OnGetModels()", "Language Translation - Get models response: {0}", data);
}
```





### Create a model
Uploads a TMX glossary file on top of a domain to customize a translation model.Depending on the size of the file, training can range from minutes for a glossary to several hours for a large parallel corpus. Glossary files must be less than 10 MB. The cumulative file size of all uploaded glossary and corpus files is limited to 250 MB.
```cs
private void CreateModel()
{
  if (!_languageTranslation.CreateModel(OnCreateModel, <base-model-name>, <custom-model-name>, <glossary-filepath>))
    Log.Debug("ExampleLanguageTranslation.CreateModel()", "Failed to create model.");
}

private void OnCreateModel(TranslationModel model, string data)
{
  Log.Debug("ExampleLanguageTranslation.OnCreateModel()", "Language Translation - Create model response: {0}", data);
}
```





### Get a model details
Returns information, including training status, about a specified translation model.
```cs
private void GetModel()
{
  if (!_languageTranslation.GetModel(OnGetModel, <custom-language-model-id>))
    Log.Debug("ExampleLanguageTranslation.GetModel()", "Failed to get model.");
}

private void OnGetModel(TranslationModel model, string data)
{
  Log.Debug("ExampleLanguageTranslation.OnGetModel()", "Language Translation - Get model response: {0}", data);
}
```





### Delete a model
Deletes trained translation models.
```cs
private void DeleteModel()
{
  if (!_languageTranslation.DeleteModel(OnDeleteModel, <custom-language-model-id>))
    Log.Debug("ExampleLanguageTranslation.DeleteModel()", "Failed to delete model.");
}

private void OnDeleteModel(bool success, string data)
{
  Log.Debug("ExampleLanguageTranslation.OnDeleteModel()", "Language Translation - Delete model response: success: {0}", success);
}
```





### Translate
Translates input text from the source language to the target language.
```cs
private void Translate()
{
  if (!_languageTranslation.GetTranslation(<text-to-translate>, <from-language>, <to-language>, OnGetTranslation))
    Log.Debug("ExampleLanguageTranslation.Translate()", "Failed to translate.");
}

private void OnGetTranslation(Translations translation, string data)
{
  Log.Debug("ExampleLanguageTranslation.OnGetTranslation()", "Langauge Translation - Translate Response: {0}", data);
}
```




### Identify language
Identify the language in which a text is written.
```cs
private void Identify()
{
  if (!_languageTranslation.Identify(OnIdentify, <text-to-identify>))
    Log.Debug("ExampleLanguageTranslation.Identify()", "Failed to identify language.");
}

private void OnIdentify(string lang, string data)
{
  Log.Debug("ExampleLanguageTranslation.OnIdentify()", "Language Translation - Identify response: {0}", data);
}
```





### Identifiable languages
Return the list of languages it can detect.
```cs
private void GetLanguages()
{
  if (!_languageTranslation.GetLanguages(OnGetLanguages))
    Log.Debug("ExampleLanguageTranslation.GetLanguages()", "Failed to get languages.");
}

private void OnGetLanguages(Languages languages, string data)
{
  Log.Debug("ExampleLanguageTranslation.OnGetLanguages()", "Language Translation - Get languages response: {0}", data);
}
```





[language_Translation]: https://www.ibm.com/watson/services/language-translator/
