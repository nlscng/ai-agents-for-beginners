[![How to Design Good AI Agents](../../../translated_images/pa/lesson-4-thumbnail.546162853cb3daff.webp)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(ਇਸ ਪਾਠ ਦੀ ਵੀਡੀਓ ਦੇਖਣ ਲਈ ਉਪਰ ਦਿੱਤੀ ਤਸਵੀਰ 'ਤੇ ਕਲਿੱਕ ਕਰੋ)_

# ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ

ਟੂਲ ਦਿਲਚਸਪ ਹਨ ਕਿਉਂਕਿ ਇਹ ਏਆਈ ਏਜੰਟਾਂ ਨੂੰ ਵਿਆਪਕ ਸਮਰੱਥਾਵਾਂ ਦੇਣ ਦੇ ਯੋਗ ਬਣਾਉਂਦੇ ਹਨ। ਏਜੰਟ ਕੋਲ ਸੀਮਤ ਕਾਰਵਾਈਆਂ ਕਰਨ ਦਾ ਸਮਰੱਥਾ ਹੋਣ ਦੀ ਬਜਾਏ, ਇੱਕ ਟੂਲ ਜੋੜ ਕੇ, ਹੁਣ ਏਜੰਟ ਵੱਡੀ ਸੰਖਿਆ ਵਿਚ ਕਾਰਵਾਈਆਂ ਕਰ ਸਕਦਾ ਹੈ। ਇਸ ਅਧਿਆਏ ਵਿੱਚ, ਅਸੀਂ ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਉਤੇ ਚਰਚਾ ਕਰਾਂਗੇ, ਜੋ ਦੱਸਦਾ ਹੈ ਕਿ ਏਆਈ ਏਜੰਟ ਕਿਸ ਤਰ੍ਹਾਂ ਖਾਸ ਟੂਲਾਂ ਨੂੰ ਆਪਣੇ ਟੀਚਿਆਂ ਨੂੰ ਪ੍ਰਾਪਤ ਕਰਨ ਲਈ ਵਰਤ ਸਕਦੇ ਹਨ।

## ਪਰਿਚਯ

ਇਸ ਪਾਠ ਵਿੱਚ, ਅਸੀਂ ਹੇਠ ਲਿਖੇ ਪ੍ਰਸ਼ਨਾਂ ਦੇ ਜਵਾਬ ਲੱਭਣ ਦੀ ਕੋਸ਼ਿਸ਼ ਕਰ ਰਹੇ ਹਾਂ:

- ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਕੀ ਹੈ?
- ਇਹ ਕਿਹੜੇ ਉਪਯੋਗ ਕੇਸਾਂ ਤੇ ਲਾਗੂ ਕੀਤਾ ਜਾ ਸਕਦਾ ਹੈ?
- ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਨੂੰ ਲਾਗੂ ਕਰਨ ਲਈ ਕਿਹੜੇ ਤੱਤ/ਬਿਲਡਿੰਗ ਬਲਾਕ ਲੋੜੀਂਦੇ ਹਨ?
- ਭਰੋਸੇਮੰਦ ਏਆਈ ਏਜੰਟ ਬਣਾਉਣ ਲਈ ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਦੇ ਖਾਸ ਧਿਆਨ ਦੇਣ ਵਾਲੇ ਮੁੱਦੇ ਕੀ ਹਨ?

## ਸਿੱਖਣ ਦੇ ਲੱਖ

ਇਸ ਪਾਠ ਨੂੰ ਪੂਰਾ ਕਰਨ ਤੋਂ ਬਾਅਦ, ਤੁਸੀਂ ਇਹ ਯੋਗ ਹੋ ਜਾਵੋਗੇ:

- ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਅਤੇ ਇਸਦਾ ਉਦੇਸ਼ ਪਰਿਭਾਸ਼ਿਤ ਕਰਨਾ।
- ਉਹ ਉਪਯੋਗ ਕੇਸਾਂ ਦੀ ਪਹਚਾਣ ਕਰਨਾ ਜਿੱਥੇ ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਲਾਗੂ ਹੋ ਸਕਦਾ ਹੈ।
- ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਲਾਗੂ ਕਰਨ ਲਈ ਮੁੱਖ ਤੱਤਾਂ ਨੂੰ ਸਮਝਣਾ।
- ਇਸ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹੋਏ ਏਆਈ ਏਜੰਟਾਂ ਵਿੱਚ ਭਰੋਸੇਯੋਗਤਾ ਨਿਸ਼ਚਿਤ ਕਰਨ ਵਾਲੀਆਂ ਚਿੰਤਾਵਾਂ ਦੀ ਪਹਚਾਣ।

## ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਕੀ ਹੈ?

**ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ** LLMs ਨੂੰ ਇਹ ਯੋਗਤਾ ਦੇਣ 'ਤੇ ਧਿਆਨ ਦੇਂਦਾ ਹੈ ਕਿ ਉਹ ਬਾਹਰੀ ਟੂਲਾਂ ਨਾਲ ਪਰਸਪਰ ਪ੍ਰਭਾਵ ਕਰ ਸਕਣ ਤਾਂ ਜੋ ਖਾਸ ਟੀਚਿਆਂ ਨੂੰ ਪ੍ਰਾਪਤ ਕੀਤਾ ਜਾ ਸਕੇ। ਟੂਲ ਕੋਡ ਹੁੰਦੇ ਹਨ ਜੋ ਇੱਕ ਏਜੰਟ ਦੁਆਰਾ ਕਾਰਵਾਈ ਕਰਨ ਲਈ ਚਲਾਏ ਜਾ ਸਕਦੇ ਹਨ। ਇੱਕ ਟੂਲ ਸਧਾਰਣ ਫੰਕਸ਼ਨ ਜਿਵੇਂ ਕਿ ਕੈਲਕੂਲੇਟਰ ਹੋ ਸਕਦਾ ਹੈ, ਜਾਂ ਤੀਜੇ ਪਾਸੇ ਦੀ ਸੇਵਾ ਦਾ API ਕਾਲ ਜਿਵੇਂ ਕਿ ਸਟਾਕ ਕੀਮਤ ਜਾਂ ਮੌਸਮ ਦੀ ਭਵਿੱਖਵाणी। ਏਆਈ ਏਜੰਟਾਂ ਦੇ ਸੰਦਰਭ ਵਿੱਚ, ਟੂਲਾਂ ਨੂੰ ਆਮ ਤੌਰ 'ਤੇ **ਮਾਡਲ-ਜੈਨੀਰੇਟ ਕੀਤੀਆਂ ਫੰਕਸ਼ਨ ਕਾਲਾਂ** ਦੇ ਜਵਾਬ ਵਿੱਚ ਚਲਾਇਆ ਜਾਂਦਾ ਹੈ।

## ਇਹ ਕਿਹੜੇ ਉਪਯੋਗ ਕੇਸਾਂ ਤੇ ਲਾਗੂ ਕੀਤਾ ਜਾ ਸਕਦਾ ਹੈ?

ਏਆਈ ਏਜੰਟ ਟੂਲਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਜ਼ਟਿਲ ਕਾਰਜ ਪੂਰੇ ਕਰ ਸਕਦੇ ਹਨ, ਜਾਣਕਾਰੀ ਪ੍ਰਾਪਤ ਕਰ ਸਕਦੇ ਹਨ ਜਾਂ ਫੈਸਲੇ ਲੈ ਸਕਦੇ ਹਨ। ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਪ੍ਰਚੁਰਤ ਤੌਰ 'ਤੇ ਬਾਹਰੀ ਸਿਸਟਮਾਂ ਦੇ ਨਾਲ ਗਤੀਸ਼ੀਲ ਪਰਸਪਰ ਪ੍ਰਭਾਵ ਦੀ ਲੋੜ ਵਾਲੀਆਂ ਸਥਿਤੀਆਂ ਵਿੱਚ ਵਰਤਿਆ ਜਾਂਦਾ ਹੈ, ਜਿਵੇਂ ਕਿ ਡੈਟਾਬੇਸ, ਵੈੱਬ ਸੇਵਾਵਾਂ ਜਾਂ ਕੋਡ ਇੰਟਰਪ੍ਰੀਟਰ। ਇਹ ਸਮਰੱਥਾ ਹੇਠ ਲਿਖੇ ਮੁੱਖ ਉਪਯੋਗ ਕੇਸਾਂ ਲਈ ਲਾਭਦਾਇਕ ਹੈ:

- **ਗਤੀਸ਼ੀਲ ਜਾਣਕਾਰੀ ਪ੍ਰਾਪਤੀ:** ਏਜੰਟ ਬਾਹਰੀ API ਜਾਂ ਡੈਟਾਬੇਸ ਨੂੰ ਪੁੱਛਗਿੱਛ ਕਰ ਕੇ ਤਾਜ਼ਾ ਡਾਟਾ ਲੈ ਸਕਦੇ ਹਨ (ਜਿਵੇਂ ਕਿ SQLite ਡੈਟਾਬੇਸ ਵਿੱਚ ਡਾਟਾ ਵਿਸ਼ਲੇਸ਼ਣ ਲਈ ਪੁੱਛਗਿੱਛ, ਸਟਾਕ ਕੀਮਤਾਂ ਜਾਂ ਮੌਸਮ ਦੀ ਜਾਣਕਾਰੀ ਲੈਣਾ)।
- **ਕੋਡ ਚਲਾਉਣਾ ਅਤੇ ਵਿਆਖਿਆ:** ਏਜੰਟ ਗਣਿਤੀ ਸਮੱਸਿਆਵਾਂ ਹੱਲ ਕਰਨ, ਰਿਪੋਰਟ ਤਿਆਰ ਕਰਨ ਜਾਂ ਸਿਮੂਲੇਸ਼ਨ ਕਰਨ ਲਈ ਕੋਡ ਜਾਂ ਸਕ੍ਰਿਪਟ ਚਲਾ ਸਕਦੇ ਹਨ।
- **ਵਰਕਫਲੋ ਸਵੈਚਾਲਨ:** ਟਾਸਕ ਸ਼ੈਡਿਊਲਰ, ਈਮੇਲ ਸੇਵਾਵਾਂ ਜਾਂ ਡੇਟਾ ਪਾਈਪਲਾਈਨਾਂ ਵਰਗੇ ਟੂਲਾਂ ਨੂੰ ਜੋੜ ਕੇ ਦੁਹਰਾਏ ਜਾਣ ਵਾਲੇ ਜਾਂ ਕਈ ਕਦਮਾਂ ਵਾਲੇ ਵਰਕਫਲੋਜ਼ ਦੀ ਸਵੈਚਾਲਨ ਕਰੋ।
- **ਗਾਹਕ ਸਹਾਇਤਾ:** ਏਜੰਟ CRM 시스템ਾਂ, ਟਿੱਕਟਿੰਗ ਪਲੇਟਫਾਰਮਾਂ ਜਾਂ ਗਿਆਨ ਅਧਾਰ ਨਾਲ ਪਰਸਪਰ ਲੱਭ ਕਰ ਸਕਦੇ ਹਨ ਤਾਂ ਜੋ ਯੂਜ਼ਰ ਪੁੱਛਗਿੱਛਾਂ ਨੂੰ ਹੱਲ ਕੀਤਾ ਜਾ ਸਕੇ।
- **ਸਮੱਗਰੀ ਬਣਾਉਣ ਅਤੇ ਸੋਧ:** ਏਜੰਟ ਗ੍ਰਾਮਰ ਚੈਕਰ, ਟੈਕਸਟ ਸੰਖੇਪਕ ਜਾਂ ਸਮੱਗਰੀ ਸੁਰੱਖਿਆ ਮੁਲਾਂਕਣਕਰਤਾ ਵਰਗੇ ਟੂਲਾਂ ਦੀ ਸਹਾਇਤਾ ਨਾਲ ਸਮੱਗਰੀ ਬਣਾਉਣ ਵਾਲੇ ਕੰਮਾਂ ਵਿੱਚ ਸਹਾਇਤਾ ਕਰ ਸਕਦੇ ਹਨ।

## ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਨੂੰ ਲਾਗੂ ਕਰਨ ਲਈ ਕਿਹੜੇ ਤੱਤ/ਬਿਲਡਿੰਗ ਬਲਾਕ ਲੋੜੀਂਦੇ ਹਨ?

ਇਹ ਬਿਲਡਿੰਗ ਬਲਾਕ ਏਆਈ ਏਜੰਟ ਨੂੰ ਵਿਆਪਕ ਕਾਰਜ ਕਰਨ ਯੋਗ ਬਣਾਉਂਦੇ ਹਨ। ਅਸੀਂ ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਲਾਗੂ ਕਰਨ ਲਈ ਜਰੂਰੀ ਮੁੱਖ ਤੱਤਾਂ ਨੂੰ ਵੇਖਦੇ ਹਾਂ:

- **ਫੰਕਸ਼ਨ/ਟੂਲ ਸਕੀਮਾ**: ਉਪਲਬਧ ਟੂਲਾਂ ਦੀ ਵਿਸਥਾਰ ਨਾਲ ਪਰਿਭਾਸ਼ਾ, ਫੰਕਸ਼ਨ ਦਾ ਨਾਮ, ਉਦੇਸ਼, ਲੋੜੀਂਦੇ ਪੈਰਾਮੀਟਰ ਅਤੇ ਉਮੀਦ ਕੀਤੀ ਨਤੀਜੇ। ਇਹ ਸਕੀਮਾਂ LLM ਨੂੰ ਇਹ ਸਮਝਣ ਵਿੱਚ ਸਹਾਇਤਾ ਦਿੰਦੇ ਹਨ ਕਿ ਕਿਹੜੇ ਟੂਲ ਉਪਲਬਧ ਹਨ ਅਤੇ ਕਿਵੇਂ ਵੈਧ ਬੇਨਤੀਆਂ ਬਣਾਉਣੀਆਂ ਹਨ।

- **ਫੰਕਸ਼ਨ ਚਲਾਉਣ ਵਾਲਾ ਲੋਜਿਕ**: ਵਰਤੋਂਕਾਰ ਦੀ ਭਾਵਨਾ ਅਤੇ ਗੱਲਬਾਤ ਸੰਦਰਭ ਦੇ ਆਧਾਰ 'ਤੇ ਟੂਲਾਂ ਨੂੰ ਕਿਵੇਂ ਅਤੇ ਕਦੋਂ ਬੁਲਾਇਆ ਜਾਂਦਾ ਹੈ, ਇਹ ਨਿਰਧਾਰਿਤ ਕਰਦਾ ਹੈ। ਇਸ ਵਿੱਚ ਯੋਜਨਾ ਬਣਾਉਣ ਵਾਲੇ ਮਾਡਿਊਲ, ਰੂਟਿੰਗ ਪ੍ਰਣਾਲੀ ਜਾਂ ਸ਼ਰਤੀ ਪ੍ਰਵਾਹ ਸ਼ਾਮਲ ਹੋ ਸਕਦੇ ਹਨ ਜੋ ਡਾਇਨੇਮਿਕ ਟੂਲ ਵਰਤੋਂ ਨਿਰਧਾਰਤ ਕਰਦੇ ਹਨ।

- **ਸੰਦੇਸ਼ ਹੈਂਡਲਿੰਗ ਸਿਸਟਮ**: ਉਹ ਭਾਗ ਜੋ ਵਰਤੋਂਕਾਰ ਦੀਆਂ ਇਨਪੁੱਟਾਂ, LLM ਦੇ ਜਵਾਬਾਂ, ਟੂਲ ਕਾਲਾਂ ਅਤੇ ਟੂਲ ਨਤੀਜਿਆਂ ਵਿਚਕਾਰ ਗੱਲਬਾਤ ਦਾ ਪ੍ਰਬੰਧ ਕਰਦੇ ਹਨ।

- **ਟੂਲ ਇੰਟਿਗ੍ਰੇਸ਼ਨ ਫਰੇਮਵਰਕ**: ਹਿੱਸਾ ਜੋ ਏਜੰਟ ਨੂੰ ਵੱਖ-ਵੱਖ ਟੂਲਾਂ ਨਾਲ ਜੋੜਦਾ ਹੈ, ਚਾਹੇ ਉਹ ਸਧਾਰਣ ਫੰਕਸ਼ਨ ਹੋਣ ਜਾਂ ਜਟਿਲ ਬਾਹਰੀ ਸੇਵਾਵਾਂ।

- **ਗਲਤੀ ਸੰਭਾਲ ਅਤੇ ਵੈਰਿਫਿਕੇਸ਼ਨ**: ਟੂਲ ਚਲਾਉਣ ਵਿੱਚ ਆਉਣ ਵਾਲੀਆਂ ਅਸਫਲਤਾਵਾਂ, ਪੈਰਾਮੀਟਰਾਂ ਦੀ ਵੈਧਤਾ ਜਾਂ ਅਣਪੇक्षित ਜਵਾਬਾਂ ਦਾ ਪ੍ਰਬੰਧ ਕਰਨ ਵਾਲੇ ਮਕੈਨੀਜ਼ਮ।

- **ਸਥਿਤੀ ਪ੍ਰਬੰਧਨ**: ਗੱਲਬਾਤ ਸੰਦਰਭ, ਪਹਿਲਾਂ ਹੋਈ ਟੂਲ ਇੰਟੇਰੈਕਸ਼ਨਾਂ ਅਤੇ ਸਥਾਈ ਡਾਟਾ ਨੂੰ ਟਰੈਕ ਕਰਨਾ ਤਾਂ ਜੋ ਕਈ ਵਾਰੀ ਚੱਲ ਰਹੀਆਂ ਗੱਲਬਾਤਾਂ ਵਿੱਚ ਸਥਿਰਤਾ ਬਣਾ ਰਹੇ।

ਹੁਣ ਅਸੀਂ ਫੰਕਸ਼ਨ/ਟੂਲ ਕਾਲਿੰਗ ਨੂੰ ਵਧੇਰੇ ਵੇਰਵੇ ਨਾਲ ਵੇਖਾਂਗੇ।

### ਫੰਕਸ਼ਨ/ਟੂਲ ਕਾਲਿੰਗ

ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਵੱਡੇ ਭਾਸ਼ਾ ਮਾਡਲਾਂ (LLMs) ਨੂੰ ਟੂਲਾਂ ਨਾਲ ਪਰਸਪਰ ਪ੍ਰਭਾਵ ਕਰਨ ਦਾ ਮੁੱਖ ਤਰੀਕਾ ਹੈ। ਅਕਸਰ ਤੁਸੀਂ 'ਫੰਕਸ਼ਨ' ਅਤੇ 'ਟੂਲ' ਨੂੰ ਬਦਲ-ਬਦਲ ਕੇ ਵਰਤਿਆ ਵੇਖੋਗੇ ਕਿਉਂਕਿ 'ਫੰਕਸ਼ਨ' (ਪੁਨਰਵਰਤਨਯੋਗ ਕੋਡ ਦੇ ਬਲਾਕ) ਉਹ 'ਟੂਲ' ਹਨ ਜੋ ਏਜੰਟ ਕਾਰਜ ਕਰਨ ਲਈ ਵਰਤਦੇ ਹਨ। ਕਿਸੇ ਫੰਕਸ਼ਨ ਦਾ ਕੋਡ ਚਲਾਉਣ ਲਈ, LLM ਨੂੰ ਵਰਤੋਂਕਾਰ ਦੀ ਬੇਨਤੀ ਦਾ ਫੰਕਸ਼ਨ ਦੀ ਵਿਆਖਿਆ ਨਾਲ ਤੁਲਨਾ ਕਰਨੀ ਪੈਂਦੀ ਹੈ। ਇਸ ਲਈ ਸਾਰੇ ਉਪਲਬਧ ਫੰਕਸ਼ਨਾਂ ਦੀਆਂ ਵਿਆਖਿਆਵਾਂ ਵਾਲਾ ਇਕ ਸਕੀਮਾ LLM ਨੂੰ ਭੇਜਿਆ ਜਾਂਦਾ ਹੈ। ਫਿਰ LLM ਟਾਸਕ ਲਈ ਸਭ ਤੋਂ ਉਚਿਤ ਫੰਕਸ਼ਨ ਚੁਣਦਾ ਹੈ ਅਤੇ ਇਸਦੇ ਨਾਮ ਅਤੇ ਪੈਰਾਮੀਟਰ ਵਾਪਸ ਕਰਦਾ ਹੈ। ਚੁਣਿਆ ਹੋਇਆ ਫੰਕਸ਼ਨ ਚਲਾਇਆ ਜਾਂਦਾ ਹੈ, ਉਸਦੀ ਜਵਾਬੀ ਸੰਦੇਸ਼ LLM ਨੂੰ ਭੇਜੀ ਜਾਂਦੀ ਹੈ, ਜਿਸਦੇ ਆਧਾਰ 'ਤੇ LLM ਵਰਤੋਂਕਾਰ ਦੀ ਬੇਨਤੀ ਦਾ ਜਵਾਬ ਦਿੰਦਾ ਹੈ।

ਏਜੰਟਾਂ ਲਈ ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਲਾਗੂ ਕਰਨ ਲਈ ਤੁਹਾਨੂੰ ਬਰਕਰਾਰ ਕਰਨਾ ਪਵੇਗਾ:

1. ਇੱਕ ਐਸਾ LLM ਮਾਡਲ ਜੋ ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਦਾ ਸਮਰਥਨ ਕਰਦਾ ਹੋਵੇ
2. ਫੰਕਸ਼ਨ ਵੇਰਵਿਆਂ ਵਾਲਾ ਸਕੀਮਾ
3. ਹਰ ਫੰਕਸ਼ਨ ਦਾ ਕੋਡ ਜੋ ਵੇਰਵਾ ਦਿੱਤਾ ਗਿਆ ਹੈ

ਚਲੋ ਸ਼ਹਿਰ ਵਿੱਚ ਮੁਲਕਤ ਸਮਾਂ ਪ੍ਰਾਪਤ ਕਰਨ ਦੇ ਉਦਾਹਰਨ ਨਾਲ ਸਮਝਾਈਏ:

1. **ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਦਾ ਸਮਰਥਨ ਕਰਨ ਵਾਲਾ LLM ਆਰੰਭ ਕਰੋ:**

   ਸਾਰੇ ਮਾਡਲ ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਨੂੰ ਸਪੋਰਟ ਨਹੀਂ ਕਰਦੇ, ਇਸलिए ਇਹ ਜ਼ਰੂਰੀ ਹੈ ਕਿ ਤੁਸੀਂ ਚੈੱਕ ਕਰੋ ਕਿ ਤੁਸੀਂ ਜਿਹੜਾ LLM ਵਰਤ ਰਹੇ ਹੋ ਉਹ ਇਸ ਨੂੰ ਸਹਾਇਤਾ ਦਿੰਦਾ ਹੈ। <a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">ਅਜ਼ੁਰ ਓਪਨਏਆਈ</a> ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਦਾ ਸਮਰਥਨ ਕਰਦਾ ਹੈ। ਅਸੀਂ ਅਜ਼ੁਰ ਓਪਨਏਆਈ ਕਲਾਇਂਟ ਨੂੰ ਆਰੰਭ ਕਰਕੇ ਸ਼ੁਰੂ ਕਰ ਸਕਦੇ ਹਾਂ।

    ```python
    # ਏਜ਼ਯੂਰ ਓਪਨਏਆਈ ਕਲਾਇੰਟ ਨੂੰ ਸ਼ੁਰੂ ਕਰੋ
    client = AzureOpenAI(
        azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"), 
        api_key=os.getenv("AZURE_OPENAI_API_KEY"),  
        api_version="2024-05-01-preview"
    )
    ```

1. **ਫੰਕਸ਼ਨ ਸਕੀਮਾ ਬਣਾਓ:**

   ਅਗਲਾ ਕਦਮ ਇੱਕ JSON ਸਕੀਮਾ ਨੂੰ ਪਰਿਭਾਸ਼ਿਤ ਕਰਨਾ ਹੈ ਜਿਸ ਵਿੱਚ ਫੰਕਸ਼ਨ ਦਾ ਨਾਮ, ਇਹ ਕੀ ਕਰਦਾ ਹੈ ਇਸ ਦੀ ਵਰਣਨਾ ਅਤੇ ਫੰਕਸ਼ਨ ਪੈਰਾਮੀਟਰਾਂ ਦੇ ਨਾਮ ਅਤੇ ਵਰਣਨਾ ਸ਼ਾਮਲ ਹਨ।
   ਅਸੀਂ ਫਿਰ ਇਸ ਸਕੀਮਾ ਨੂੰ ਕਲਾਇਂਟ ਨੂੰ ਭੇਜਾਂਗੇ ਜੋ ਪਹਿਲਾਂ ਬਣਾਇਆ ਗਿਆ ਸੀ, ਅਤੇ ਵਰਤੋਂਕਾਰ ਦੀ ਬੇਨਤੀ ਨੂੰ ਵੀ ਜੋ ਸੈਨ ਫ੍ਰਾਂਸਿਸਕੋ ਵਿੱਚ ਸਮਾਂ ਲੱਭ ਰਿਹਾ ਹੈ। ਮਹੱਤਵਪੂਰਣ ਗੱਲ ਇਹ ਹੈ ਕਿ **ਟੂਲ ਕਾਲ** ਹੀ ਵਾਪਸ ਆਉਂਦਾ ਹੈ, ਸਵਾਲ ਦਾ ਅੰਤਿਮ ਜਵਾਬ ਨਹੀਂ। ਜਿਵੇਂ ਪਹਿਲਾਂ ਕਿਹਾ ਗਿਆ, LLM ਉਸ ਫੰਕਸ਼ਨ ਦਾ ਨਾਮ ਵਾਪਸ ਕਰਦਾ ਹੈ ਜੋ ਉਸਨੇ ਇਸ ਕਾਰਜ ਲਈ ਚੁਣਿਆ, ਅਤੇ ਜਿਹੜੇ ਪੈਰਾਮੀਟਰ ਉਸਨੂੰ ਦਿੱਤੇ ਜਾਣਗੇ।

    ```python
    # ਮਾਡਲ ਲਈ ਫੰਕਸ਼ਨ ਦਾ ਵਰਣਨ ਪੜ੍ਹਨ ਲਈ
    tools = [
        {
            "type": "function",
            "function": {
                "name": "get_current_time",
                "description": "Get the current time in a given location",
                "parameters": {
                    "type": "object",
                    "properties": {
                        "location": {
                            "type": "string",
                            "description": "The city name, e.g. San Francisco",
                        },
                    },
                    "required": ["location"],
                },
            }
        }
    ]
    ```
   
    ```python
  
    # ਸ਼ੁਰੂਆਤੀ ਉਪਭੋਗਤਾ ਸੁਨੇਹਾ
    messages = [{"role": "user", "content": "What's the current time in San Francisco"}] 
  
    # ਪਹਿਲੀ ਏਪੀਆਈ ਕਾਲ: ਮਾਡਲ ਨੂੰ ਫੰਕਸ਼ਨ ਦੇ ਇਸਤੇਮਾਲ ਲਈ ਪੁੱਛੋ
      response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
          tools=tools,
          tool_choice="auto",
      )
  
      # ਮਾਡਲ ਦੇ ਜਵਾਬ ਨੂੰ ਪ੍ਰਕਿਰਿਆ ਕਰੋ
      response_message = response.choices[0].message
      messages.append(response_message)
  
      print("Model's response:")  

      print(response_message)
  
    ```

    ```bash
    Model's response:
    ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
    ```
  
1. **ਟਾਸਕ ਕਰਨ ਲਈ ਲੋੜੀਂਦਾ ਫੰਕਸ਼ਨ ਕੋਡ:**

   ਹੁਣ ਜਦੋਂ ਕਿ LLM ਨੇ ਚੁਣਿਆ ਹੈ ਕਿ ਕਿਸ ਫੰਕਸ਼ਨ ਨੂੰ ਚਲਾਉਣਾ ਹੈ, ਉਸ ਟਾਸਕ ਨੂੰ ਕਰਨ ਵਾਲਾ ਕੋਡ ਲਿਖਿਆ ਅਤੇ ਚਲਾਇਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ।
   ਅਸੀਂ ਪਾਈਥਨ ਵਿੱਚ ਮੌਜੂਦਾ ਸਮਾਂ ਪ੍ਰਾਪਤ ਕਰਨ ਲਈ ਕੋਡ ਲਿਖ ਸਕਦੇ ਹਾਂ। ਅਸੀਂ ਇਹ ਵੀ ਕੋਡ ਲਿਖਣਾ ਪਵੇਗਾ ਜੋ response_message ਤੋਂ ਨਾਮ ਅਤੇ ਪੈਰਾਮੀਟਰ ਨਿਕਾਲਦਾ ਹੈ ਤਾਂ ਜੋ ਅੰਤਿਮ ਨਤੀਜਾ ਮਿਲ ਸਕੇ।

    ```python
      def get_current_time(location):
        """Get the current time for a given location"""
        print(f"get_current_time called with location: {location}")  
        location_lower = location.lower()
        
        for key, timezone in TIMEZONE_DATA.items():
            if key in location_lower:
                print(f"Timezone found for {key}")  
                current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
                return json.dumps({
                    "location": location,
                    "current_time": current_time
                })
      
        print(f"No timezone data found for {location_lower}")  
        return json.dumps({"location": location, "current_time": "unknown"})
    ```

     ```python
     # ਫੰਕਸ਼ਨ ਕਾਲਾਂ ਸੰਭਾਲੋ
      if response_message.tool_calls:
          for tool_call in response_message.tool_calls:
              if tool_call.function.name == "get_current_time":
     
                  function_args = json.loads(tool_call.function.arguments)
     
                  time_response = get_current_time(
                      location=function_args.get("location")
                  )
     
                  messages.append({
                      "tool_call_id": tool_call.id,
                      "role": "tool",
                      "name": "get_current_time",
                      "content": time_response,
                  })
      else:
          print("No tool calls were made by the model.")  
  
      # ਦੂਜਾ API ਕਾਲ: ਮਾਡਲ ਤੋਂ ਆਖਰੀ ਜਵਾਬ ਲਓ
      final_response = client.chat.completions.create(
          model=deployment_name,
          messages=messages,
      )
  
      return final_response.choices[0].message.content
     ```

     ```bash
      get_current_time called with location: San Francisco
      Timezone found for san francisco
      The current time in San Francisco is 09:24 AM.
     ```

ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਜ਼ਿਆਦਾਤਰ, ਜੇ ਨਾ ਤਾਂ ਸਾਰੇ ਏਜੰਟ ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਵਿੱਚ ਮੁੱਖ ਭੂਮਿਕਾ ਨਿਭਾਉਂਦਾ ਹੈ, ਪਰ ਇਸ ਨੂੰ ਸਿਰੇ ਤੋਂ ਲਾਗੂ ਕਰਨਾ ਕਈ ਵਾਰੀ ਚੁਣੌਤੀ ਭਰਿਆ ਹੁੰਦਾ ਹੈ।
ਜਿਵੇਂ ਅਸੀਂ [ਪਾਠ 2](../../../02-explore-agentic-frameworks) ਵਿੱਚ ਸਿੱਖਿਆ, ਏਜੰਟਿਕ ਫਰੇਮਵਰਕਾਂ ਸਾਡੇ ਲਈ ਪਹਿਲਾਂ ਹੀ ਬਨਾਏ ਹੋਏ ਬਿਲਡਿੰਗ ਬਲਾਕ ਪ੍ਰਦਾਨ ਕਰਦੇ ਹਨ ਜੋ ਟੂਲ ਯੂਜ਼ ਨੂੰ ਲਾਗੂ ਕਰਨ ਲਈ ਸਹਾਇਕ ਹੁੰਦੇ ਹਨ।

## ਏਜੰਟਿਕ ਫਰੇਮਵਰਕਾਂ ਨਾਲ ਟੂਲ ਯੂਜ਼ ਦੇ ਉਦਾਹਰਣ

ਹੇਠਾਂ ਕੁਝ ਉਦਾਹਰਣ ਹਨ ਕਿ ਤੁਸੀਂ ਵੱਖ-ਵੱਖ ਏਜੰਟਿਕ ਫਰੇਮਵਰਕਾਂ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਨੂੰ ਕਿਵੇਂ ਲਾਗੂ ਕਰ ਸਕਦੇ ਹੋ:

### ਸੇਮੈਂਟਿਕ ਕਰਨਲ

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">ਸੇਮੈਂਟਿਕ ਕਰਨਲ</a> .NET, ਪਾਈਥਨ, ਅਤੇ ਜਾਵਾ ਵਿਕਾਸਕਾਰਾਂ ਲਈ ਇੱਕ ਖੁੱਲਾ ਸਰੋਤ ਏਆਈ ਫਰੇਮਵਰਕ ਹੈ ਜੋ ਵੱਡੇ ਭਾਸ਼ਾ ਮਾਡਲਾਂ (LLMs) ਨਾਲ ਕੰਮ ਕਰਦਾ ਹੈ। ਇਹ ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਦੀ ਪ੍ਰਕਿਰਿਆ ਨੂੰ ਆਸਾਨ ਬਣਾਉਂਦਾ ਹੈ ਕਿਉਂਕਿ ਇਹ ਆਪਣੇ ਆਪ ਹੀ ਤੁਹਾਡੇ ਫੰਕਸ਼ਨਾਂ ਅਤੇ ਉਨ੍ਹਾਂ ਦੇ ਪੈਰਾਮੀਟਰਾਂ ਦੀ ਵਰਣਨਾ ਮਾਡਲ ਨੂੰ ਕਰਦਾ ਹੈ ਜਿਹੜਾ ਕਿ <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">ਸੀਰੀਅਲਾਈਜ਼ਿੰਗ</a> ਕਹਾਉਂਦਾ ਹੈ। ਇਹ ਮਾਡਲ ਅਤੇ ਤੁਹਾਡੇ ਕੋਡ ਵਿਚਕਾਰ ਵਾਪਸੀ ਗੱਲਬਾਤ ਦਾ ਪ੍ਰਬੰਧ ਵੀ ਕਰਦਾ ਹੈ। ਸੇਮੈਂਟਿਕ ਕਰਨਲ ਵਰਗਾ ਏਜੰਟਿਕ ਫਰੇਮਵਰਕ ਵਰਤਣ ਦਾ ਇੱਕ ਹੋਰ ਫਾਇਦਾ ਇਹ ਹੈ ਕਿ ਇਸ ਨਾਲ ਤੁਹਾਨੂੰ ਪਹਿਲਾਂ ਤੋਂ ਬਣਾਈਆਂ ਟੂਲਾਂ ਜਿਵੇਂ ਕਿ <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">ਫਾਈਲ ਖੋਜ</a> ਅਤੇ <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">ਕੋਡ ਇੰਟਰਪ੍ਰੀਟਰ</a> ਨੂੰ ਸਧਾਰਨ ਤਰੀਕੇ ਨਾਲ ਵਰਤਣ ਦਾ ਮੌਕਾ ਮਿਲਦਾ ਹੈ।

ਹੇਠਾਂ ਦਿੱਤਾ ਡਾਇਗ੍ਰਾਮ ਸੇਮੈਂਟਿਕ ਕਰਨਲ ਨਾਲ ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਦੀ ਪ੍ਰਕਿਰਿਆ ਨੂੰ ਦਰਸਾਉਂਦਾ ਹੈ:

![function calling](../../../translated_images/pa/functioncalling-diagram.a84006fc287f6014.webp)

ਸੇਮੈਂਟਿਕ ਕਰਨਲ ਵਿੱਚ ਫੰਕਸ਼ਨ/ਟੂਲਾਂ ਨੂੰ <a href="https://learn.microsoft.com/semantic-kernel/concepts/plugins/?pivots=programming-language-python" target="_blank">ਪਲੱਗਇਨ</a> ਕਿਹਾ ਜਾਂਦਾ ਹੈ। ਅਸੀਂ `get_current_time` ਫੰਕਸ਼ਨ ਨੂੰ ਇੱਕ ਕਲਾਸ ਵਿੱਚ ਬਦਲ ਕੇ ਪਲੱਗਇਨ ਬਣਾ ਸਕਦੇ ਹਾਂ ਜਿਸਦੇ ਅੰਦਰ ਉਹ ਫੰਕਸ਼ਨ ਹੋਵੇ। ਅਸੀਂ `kernel_function` ਡੈਕੋਰੇਟਰ ਨੂੰ ਵੀ ਇम्पੋਰਟ ਕਰ ਸਕਦੇ ਹਾਂ, ਜੋ ਫੰਕਸ਼ਨ ਦੀ ਵਰਣਨਾ ਲੈਂਦਾ ਹੈ। ਇਸ ਤੋਂ ਬਾਅਦ ਜਦੋਂ ਤੁਸੀਂ GetCurrentTimePlugin ਨਾਲ ਇੱਕ ਕਰਨਲ ਬਣਾਉਂਦੇ ਹੋ, ਕਰਨਲ ਆਪਣੇ ਆਪ ਫੰਕਸ਼ਨ ਅਤੇ ਇਸਦੇ ਪੈਰਾਮੀਟਰਾਂ ਨੂੰ ਸੀਰੀਅਲਾਈਜ਼ ਕਰਦਾ ਹੈ, ਜੋ ਸਕੀਮਾ ਬਣਾਉਂਦਾ ਹੈ ਜੋ LLM ਨੂੰ ਭੇਜਿਆ ਜਾਂਦਾ ਹੈ।

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:
    async def __init__(self, location):
        self.location = location

    @kernel_function(
        description="Get the current time for a given location"
    )
    def get_current_time(location: str = ""):
        ...

```

```python 
from semantic_kernel import Kernel

# ਕਰਨਲ ਬਣਾਓ
kernel = Kernel()

# ਪਲੱਗਇਨ ਬਣਾਓ
get_current_time_plugin = GetCurrentTimePlugin(location)

# ਪਲੱਗਇਨ ਨੂੰ ਕਰਨਲ ਵਿੱਚ ਸ਼ਾਮਲ ਕਰੋ
kernel.add_plugin(get_current_time_plugin)
```
  
### ਅਜ਼ੁਰ ਏਆਈ ਏਜੰਟ ਸੇਵਾ

<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">ਅਜ਼ੁਰ ਏਆਈ ਏਜੰਟ ਸੇਵਾ</a> ਇੱਕ ਨਵਾਂ ਏਜੰਟਿਕ ਫਰੇਮਵਰਕ ਹੈ ਜੋ ਡਿਵੈਲਪਰਾਂ ਨੂੰ ਸੁਰੱਖਿਅਤ ਤਰੀਕੇ ਨਾਲ ਉੱਚ-ਗੁਣਵੱਤਾ, ਵਿਸਤਾਰਯੋਗ ਏਆਈ ਏਜੰਟਾਂ ਬਣਾਉਣ, ਡਿਪਲੋਇ ਕਰਨ ਅਤੇ ਸਕੇਲ ਕਰਨ ਦੇ ਯੋਗ ਬਣਾਉਂਦਾ ਹੈ ਬਿਨਾਂ ਹੇਠਲੇ ਸਤਰ ਦੇ ਕੰਪਿਊਟ ਅਤੇ ਸਟੋਰੇਜ ਸਰੋਤਾਂ ਨੂੰ ਪ੍ਰਬੰਧਿਤ ਕੀਤੇ। ਇਹ ਵਿਸ਼ੇਸ਼ ਤੌਰ 'ਤੇ ਉਦਯੋਗਿਕ ਐਪਲੀਕੇਸ਼ਨਾਂ ਲਈ ਲਾਭਦਾਇਕ ਹੈ ਕਿਉਂਕਿ ਇਹ ਇੱਕ ਪੂਰੀ ਤਰ੍ਹਾਂ ਪ੍ਰਬੰਧਿਤ ਸੇਵਾ ਹੈ ਜੋ ਉਦਯੋਗਿਕ ਸਰਟੀਫਿਕੇਸ਼ਨ ਨਾਲ ਲੈਸ ਹੈ।

ਜਦੋਂ ਤੁਸੀਂ ਇਸਨੂੰ LLM API ਨਾਲ ਸਿੱਧਾ ਵਿਕਾਸ ਨਾਲ ਤੁਲਨਾ ਕਰਦੇ ਹੋ, ਅਜ਼ੁਰ ਏਆਈ ਏਜੰਟ ਸੇਵਾ ਹੇਠ ਲਿਖੇ ਲਾਭ ਦਿੰਦੀ ਹੈ:

- ਸਵੈਚਾਲਿਤ ਟੂਲ ਕਾਲਿੰਗ – ਹੁਣ ਸਰਵਰ-ਸਾਈਡ ਤੇ ਸਾਰਾ ਕੰਮ ਹੁੰਦਾ ਹੈ, ਟੂਲ ਕਾਲ ਨੂੰ ਪਾਰਸ ਕਰਨ, ਟੂਲ ਨੂੰ ਚਲਾਉਣ ਅਤੇ ਜਵਾਬ ਦਾ ਪ੍ਰਬੰਧ ਕਰਨ ਦੀ ਲੋੜ ਨਹੀਂ
- ਸੁਰੱਖਿਅਤ ਡਾਟਾ ਪ੍ਰਬੰਧਨ – ਗੱਲਬਾਤ ਪੰਜਾਬੀ ਸਥਿਤੀ ਨੂੰ ਸਾਂਭਣ ਦੀ ਬਜਾਏ ਤੁਸੀਂ ਥ੍ਰੇਡਾਂ 'ਤੇ ਭਰੋਸਾ ਕਰ ਸਕਦੇ ਹੋ ਜੋ ਸਾਰੀ ਲੋੜੀਂਦੀ ਜਾਣਕਾਰੀ ਸਟੋਰ ਕਰਦੇ ਹਨ
- ਪਹਿਲਾਂ ਤੋਂ ਬਣੇ ਹੋਏ ਟੂਲ – ਜਿਹੜੇ ਤੁਸੀਂ ਆਪਣੇ ਡਾਟਾ ਸਰੋਤਾਂ ਨਾਲ ਪਰਸਪਰ ਕਰ ਸਕਦੇ ਹੋ, ਜਿਵੇਂ Bing, ਅਜ਼ੁਰ ਏਆਈ ਖੋਜ, ਅਤੇ ਅਜ਼ੁਰ ਫਂਕਸ਼ਨਜ਼।

ਅਜ਼ੁਰ ਏਆਈ ਏਜੰਟ ਸੇਵਾ ਵਿੱਚ ਉਪਲਬਧ ਟੂਲਾਂ ਨੂੰ ਦੋ ਸ਼੍ਰੇਣੀਆਂ ਵਿੱਚ ਵੰਡਿਆ ਜਾ ਸਕਦਾ ਹੈ:

1. ਗਿਆਨ ਟੂਲ:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">ਬਿੰਗ ਖੋਜ ਨਾਲ ਗਰਾਉਂਡਿੰਗ</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">ਫਾਈਲ ਖੋਜ</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">ਅਜ਼ੁਰ ਏਆਈ ਖੋਜ</a>

2. ਕ੍ਰਿਆਟਮਕ ਟੂਲ:
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">ਕੋਡ ਇੰਟਰਪ੍ਰੀਟਰ</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI ਪ੍ਰਿਭਾਸ਼ਿਤ ਟੂਲ</a>
    - <a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">ਅਜ਼ੁਰ ਫਂਕਸ਼ਨਜ਼</a>

ਏਜੰਟ ਸੇਵਾ ਸਾਨੂੰ ਇਹ ਟੂਲ ਇਕੱਠੇ ਕਰਕੇ ਇੱਕ `ਟੂਲਸੈੱਟ` ਵਜੋਂ ਵਰਤਣ ਦੀ ਆਗਿਆ ਦਿੰਦੀ ਹੈ। ਇਹ `ਥ੍ਰੇਡ` ਦੀ ਵਰਤੋਂ ਵੀ ਕਰਦੀ ਹੈ ਜੋ ਖਾਸ ਗੱਲਬਾਤ ਦੀ ਮੈਸੇਜ ਇਤਿਹਾਸ ਨੂੰ ਟਰੈਕ ਕਰਦੇ ਹਨ।

ਕਲਪਨਾ ਕਰੋ ਕਿ ਤੁਸੀਂ Contoso ਨਾਮਕ ਕੰਪਨੀ ਵਿੱਚ ਸੇਲਜ਼ ਏਜੰਟ ਹੋ। ਤੁਸੀਂ ਇੱਕ ਗੱਲਬਾਤੀ ਏਜੰਟ ਬਣਾਉਣਾ ਚਾਹੁੰਦੇ ਹੋ ਜੋ ਤੁਹਾਡੇ ਸੇਲਜ਼ ਡਾਟਾ ਬਾਰੇ ਸਵਾਲਾਂ ਦੇ ਉੱਤਰ ਦੇ ਸਕੇ।

ਹੇਠਾਂ ਦਿੱਤੀ ਤਸਵੀਰ ਦਰਸਾਉਂਦੀ ਹੈ ਕਿ ਤੁਸੀਂ ਅਜ਼ੁਰ ਏਆਈ ਏਜੰਟ ਸੇਵਾ ਵਰਤ ਕੇ ਕਿਵੇਂ ਆਪਣੇ ਸੇਲਜ਼ ਡਾਟਾ ਦਾ ਵਿਸ਼ਲੇਸ਼ਣ ਕਰ ਸਕਦੇ ਹੋ:

![Agentic Service In Action](../../../translated_images/pa/agent-service-in-action.34fb465c9a84659e.webp)

ਸੇਵਾ ਨਾਲ ਕਿਸੇ ਵੀ ਟੂਲ ਨੂੰ ਵਰਤਣ ਲਈ ਅਸੀਂ ਕਲਾਇਂਟ ਬਣਾਕੇ ਟੂਲ ਜਾਂ ਟੂਲਸੈੱਟ ਨੂੰ ਪਰਿਭਾਸ਼ਿਤ ਕਰ ਸਕਦੇ ਹਾਂ। ਇਸਨੂੰ ਵਿਹਾਰਕ ਰੂਪ ਵਿੱਚ ਲਾਗੂ ਕਰਨ ਲਈ ਹੇਠਾਂ ਦਿੱਤੇ ਪਾਈਥਨ ਕੋਡ ਦੀ ਵਰਤੋਂ ਕਰ ਸਕਦੇ ਹਾਂ। LLM ਟੂਲਸੈੱਟ ਨੂੰ ਵੇਖ ਕੇ ਫੈਸਲਾ ਕਰੇਗਾ ਕਿ ਵਰਤੋਂਕਾਰ ਬਣਾਇਆ ਫੰਕਸ਼ਨ `fetch_sales_data_using_sqlite_query` ਨੂੰ ਵਰਤਣਾ ਹੈ ਜਾਂ ਪਹਿਲਾਂ ਤੋਂ ਬਣਾਇਆ ਕੋਡ ਇੰਟਰਪ੍ਰੀਟਰ ਉਹਦੇ ਹਿਸਾਬ ਨਾਲ।

```python 
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query # fetch_sales_data_using_sqlite_query ਫੰਕਸ਼ਨ ਜੋ fetch_sales_data_functions.py ਫਾਇਲ ਵਿੱਚ ਮਿਲ ਸਕਦਾ ਹੈ।
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# ਟੂਲਸੈੱਟ ਸ਼ੁਰੂ ਕਰੋ
toolset = ToolSet()

# fetch_sales_data_using_sqlite_query ਫੰਕਸ਼ਨ ਨਾਲ ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਏਜੰਟ ਨੂੰ ਸ਼ੁਰੂ ਕਰੋ ਅਤੇ ਇਸਨੂੰ ਟੂਲਸੈੱਟ ਵਿੱਚ ਸ਼ਾਮਲ ਕਰੋ
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# ਕੋਡ ਇੰਟਰਪ੍ਰੀਟਰ ਟੂਲ ਨੂੰ ਸ਼ੁਰੂ ਕਰੋ ਅਤੇ ਇਹਨੂੰ ਟੂਲਸੈੱਟ ਵਿੱਚ ਸ਼ਾਮਲ ਕਰੋ।
code_interpreter = code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

agent = project_client.agents.create_agent(
    model="gpt-4o-mini", name="my-agent", instructions="You are helpful agent", 
    toolset=toolset
)
```

## ਭਰੋਸੇਯੋਗ ਏਆਈ ਏਜੰਟ ਬਣਾਉਣ ਲਈ ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨ ਦੀ ਵਰਤੋਂ ਕਰਨ ਸਮੇਂ ਖ਼ਾਸ ਧਿਆਨ

LLMs ਦੁਆਰਾ ਡਾਈਨਾਮਿਕ ਤੌਰ 'ਤੇ ਬਣਾਈ ਗਈ SQL ਦੇ ਸੁਰੱਖਿਆ ਸੰਬੰਧੀ ਸੁਆਲ ਸਧਾਰਨ ਹਨ, ਖਾਸਕਰ SQL ਇੰਜੈਕਸ਼ਨ ਜਾਂ ਮਾਲਿਸ਼ਿਅਸ ਕਾਰਵਾਈਆਂ, ਜਿਵੇਂ ਡੈਟਾਬੇਸ ਡ੍ਰੌਪ ਕਰਨਾ ਜਾਂ ਛੇੜਛਾੜ ਕਰਨਾ। ਜਦਕਿ ਇਹ ਚਿੰਤਾਵਾਂ ਵਾਜਬ ਹਨ, ਇਹਨਾਂ ਨੂੰ ਡੈਟਾਬੇਸ ਦੀ ਐਕਸੈਸ ਪਰਮੀਸ਼ਨਾਂ ਨੂੰ ਢੰਗ ਨਾਲ ਕੰਫਿਗਰ ਕਰਕੇ ਅਚਿਛੀ ਤਰ੍ਹਾਂ ਘਟਾਇਆ ਜਾ ਸਕਦਾ ਹੈ। ਬਹੁਤ ਸਾਰੇ ਡੈਟਾਬੇਸਾਂ ਲਈ ਇਹ ਪঠন-ਕੇਵਲ ਅਧਿਕਾਰ (read-only) ਵਿੱਚ ਡੈਟਾਬੇਸ ਨੂੰ ਸੈਟ ਕਰਨ ਨਾਲ ਕੀਤਾ ਜਾਂਦਾ ਹੈ। ਜਿਵੇਂ PostgreSQL ਜਾਂ ਅਜ਼ੁਰ SQL ਵਰਗੀਆਂ ਡੈਟਾਬੇਸ ਸੇਵਾਵਾਂ ਵਿੱਚ, ਐਪ ਨੂੰ ਪठन-ਕੇਵਲ (SELECT) ਭੂਮਿਕਾ ਅਲਾਟ ਕੀਤੀ ਜਾ ਸਕਦੀ ਹੈ।

ਐਪ ਨੂੰ ਇੱਕ ਸੁਰੱਖਿਅਤ ਵਾਤਾਵਰਣ ਵਿੱਚ ਚਲਾਉਣ ਨਾਲ ਸੁਰੱਖਿਆ ਹੋਰ ਵਧ ਜਾਂਦੀ ਹੈ। ਉਦਯੋਗਿਕ ਸਥਿਤੀਆਂ ਵਿੱਚ, ਡਾਟਾ ਆਮ ਤੌਰ 'ਤੇ ਚਾਲੂ ਸਿਸਟਮਾਂ ਤੋਂ ਕੱਢ ਕੇ ਇੱਕ ਪਠਿਤ-ਕੇਵਲ ਡੈਟਾਬੇਸ ਜਾਂ ਡੈਟਾ ਵੇਅਰਹਾਊਸ ਵਿੱਚ ਬਦਲਿਆ ਜਾਂਦਾ ਹੈ, ਜੋ ਵਰਤੋਂਕਾਰ-ਮਿੱਤਰ ਸਕੀਮਾ ਰੱਖਦਾ ਹੈ। ਇਹ ਯਕੀਨੀ ਬਣਾਉਂਦਾ ਹੈ ਕਿ ਡਾਟਾ ਸੁਰੱਖਿਅਤ ਹੈ, ਕਾਰਗੁਜ਼ਾਰੀ ਅਤੇ ਪਹੁੰਚ ਲਈ ਭਲਕੇ ਤਰੀਕੇ ਨਾਲ ਤਿਆਰ ਹੈ ਅਤੇ ਐਪ ਦਾ ਐਕਸੈਸ ਸਹਿਮਤ ਹੈ।

## ਸੈਂਪਲ ਕੋਡਸ
- Python: [Agent Framework](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent Framework](./code_samples/04-dotnet-agent-framework.md)

## ਟੂਲ ਯੂਜ਼ ਡਿਜ਼ਾਈਨ ਪੈਟਰਨਾਂ ਬਾਰੇ ਹੋਰ ਸਵਾਲ ਹਨ?

ਹੋਰ ਸਿੱਖਣ ਵਾਲਿਆਂ ਨਾਲ ਮਿਲਣ ਲਈ, ਦਫ਼ਤਰ ਘੰਟਿਆਂ ਵਿੱਚ ਸ਼ਾਮਿਲ ਹੋਵੋ ਅਤੇ ਆਪਣੇ AI ਏਜੰਟਸ ਦੇ ਸਵਾਲਾਂ ਦੇ ਜਵਾਬ ਲਈ [Microsoft Foundry Discord](https://aka.ms/ai-agents/discord) ਵਿੱਚ ਸ਼ਾਮਿਲ ਹੋਵੋ।

## ਵਾਧੂ ਸਰੋਤ

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">ਐਜ਼ੂਅਰ AI ਏਜੰਟਸ ਸਰਵਿਸ ਵਰਕਸ਼ਾਪ</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">ਕਾਂਟੋਸੋ ਕ੍ਰੀਏਟਿਵ ਰਾਈਟਰ ਮਲਟੀ-ਏਜੰਟ ਵਰਕਸ਼ਾਪ</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">ਸੈਮੈਂਟਿਕ ਕਰਨੈਲ ਫੰਕਸ਼ਨ ਕਾਲਿੰਗ ਟਿਊਟੋਰੀਅਲ</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">ਸੈਮੈਂਟਿਕ ਕਰਨੈਲ ਕੋਡ ਅਨੁਵਾਦਕ</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">ਆਟੋਜਨ ਟੂਲਸ</a>

## ਪਿਛਲਾ ਪਾਠ

[Agentic Design Patterns ਨੂੰ ਸਮਝਣਾ](../03-agentic-design-patterns/README.md)

## ਅਗਲਾ ਪਾਠ

[Agentic RAG](../05-agentic-rag/README.md)

---

<!-- CO-OP TRANSLATOR DISCLAIMER START -->
**ਅਸਤੀਫ਼ਾ**:
ਇਹ ਦਸਤਾਵੇਜ਼ AI ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀਅਤ ਲਈ ਯਤਨ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਜਾਣੋ ਕਿ ਆਟੋਮੈਟਿਕ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸਹੀਤੀਆਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਮੂਲ ਦਸਤਾਵੇਜ਼ ਆਪਣੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਹੀ ਪ੍ਰਮਾਣਿਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਣ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ਾਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫ਼ਾਰਿਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਅਸੀਂ ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਉੱਪਜਣ ਵਾਲੀਆਂ ਕਿਸੇ ਵੀ ਗਲਤਫਹਿਮੀਆਂ ਜਾਂ ਭ੍ਰਮਾਂ ਲਈ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।
<!-- CO-OP TRANSLATOR DISCLAIMER END -->