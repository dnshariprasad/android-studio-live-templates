# Android Studio - Live Templates

####Retrofit

*Abbreviation* : **retrofit**

*Template Text* :
```
private Retrofit $name$ = new Retrofit.Builder()
        .baseUrl($url$)
        .addConverterFactory(StringConverterFactory.create())
        .addConverterFactory(GsonConverterFactory.create())
        .build();
```
*Abbreviation* : **scf**

*Template Text* :
```
public class StringConverterFactory extends Converter.Factory {
    private static final MediaType MEDIA_TYPE = MediaType.parse("text/plain");

    public static StringConverterFactory create() {
        return new StringConverterFactory();
    }

    @Override
    public Converter<ResponseBody, ?> responseBodyConverter(Type type, Annotation[] annotations, Retrofit retrofit) {
        if (String.class.equals(type)) {
            return new Converter<ResponseBody, String>() {
                @Override
                public String convert(ResponseBody value) throws IOException {
                    return value.string();
                }
            };
        }
        return null;
    }

    @Override
    public Converter<?, RequestBody> requestBodyConverter(Type type, Annotation[] parameterAnnotations, Annotation[] methodAnnotations, Retrofit retrofit) {
        if (String.class.equals(type)) {
            return new Converter<String, RequestBody>() {
                @Override
                public RequestBody convert(String value) throws IOException {
                    return RequestBody.create(MEDIA_TYPE, value);
                }
            };
        }
        return null;
    }
}
```
####GSON

*Abbreviation* : **fj**

*Template Text* :
```
public static $className$ fromJson(String jsonString) {
       return new Gson().fromJson(jsonString, $className$.class);
}
```
*Abbreviation* : **tj**

*Template Text* :
```
public JSONObject toJson() {
    String jsonRepresentation = new Gson().toJson(this, $className$.class);
    JSONObject jsonObject = null;
    try {
        jsonObject = new JSONObject(jsonRepresentation);
        } catch (JSONException e) {
            Log.e(TAG, "Error converting to JSON: " + e.getMessage());
        }
    return jsonObject;
}
```
####FRAGMENT

*Abbreviation* : **cfrag**

*Template Text* :
```
@Override
public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
    view = inflater.inflate(R.layout.$resId$, container, false);
    return view;
}
```
####Recyclerview Inflator

Abbreviation : **rvin**

Template Text :
```
View view = (LayoutInflater.from(parent.getContext())).inflate(R.layout.$resId$, parent, false);
```
*Abbreviation* : **optmenu**

*Template Text* :
```
@Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.$resId$, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        switch (item.getItemId()) {
            case R.id.$resId$:
                return true;
            default:
                return super.onOptionsItemSelected(item);
        }
    }
```
[Live Templates - Handy Reference](https://cdn-images-1.medium.com/max/2000/1*4Y_TdIYJonsLtoPgtp8-jg.png)

###Refer : 
[Android Studio Live Templates - Medium] (https://medium.com/google-developers/writing-more-code-by-writing-less-code-with-android-studio-live-templates-244f648d17c7#.ikhy6j88b)

