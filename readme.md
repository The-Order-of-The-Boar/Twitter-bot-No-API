<h1 align="center">
  Twitter Bot Sem API
</h1>


<h1 align="center">
  <img src="image/bot.png"/>
</h1>

## Como faremos isso?

- Primeiro iremos, entender um pouco sobre como podemos emular as ações humanas com um script,Se você clicar na pagina do twitter e inspecionar, e for até verá todas as request que seu navegador manda para o servidor do twitter, com base nisso você so precisa recriar essas chamada

- Para fazer isso apenas precisaremos copiar a header, que o nosso navegador enviou para a api do twitter, e com isso poderemos emular algumas ações como envio de menssagens,curtir novos tweets ou seguir os follows de outra pessoa.

- Os headers consiste na parte que contém as informações suplementares colocados no começo de um bloco de dados que estão sendo armazenados ou transmitidos, usualmente por correio eletrónico ou em pacotes dos dados emitidos através da internet, são precedidos pela informação de cabeçalho tal como o remetente e os endereços do IP do receptor.- `wikipedia`

- Recomendo usar o Google Chromer para extrair os headers.

<center>
	<img src="image/img1.png"/>
	<img src="image/img2.png"/>
	<img src="image/img3.png"/>
</center>

- Todos essa lista são as chamadas do seu navegador fez para o twitter, mandando algum `request` especifico para realizar alguma ação, como por exemplo tendo as heards e o parametro necessario podemos postar uma nova menssagem.

```python
	import request

	headers= {
    'authority': 'api.twitter.com',
    'authorization': 'Bearer UUUUUUUUUUUUUUUUUUUUUNRILgUUUUUUnNwIzUejRCOuH5E6I8xnZz4puTs%3D1Zv7ttfk8LF81IUq16cHjhLTvJu4FU33UGWWjCpTnU',
    'x-twitter-client-language': 'pt',
    'x-csrf-token': '00000000000000000000000000000000',
    'x-twitter-auth-type': 'OAuth2Session',
    'x-twitter-active-user': 'yes',
    'user-agent': 'Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4272.0 Safari/537.36',
    'content-type': 'application/x-www-form-urlencoded',
    'accept': '*/*',
    'origin': 'https://twitter.com',
    'sec-fetch-site': 'same-site',
    'sec-fetch-mode': 'cors',
    'sec-fetch-dest': 'empty',
    'referer': 'https://twitter.com/',
    'accept-language': 'pt-BR,pt;q=0.9,en-US;q=0.8,en;q=0.7',
    ......
    }

    data_post = {
      'include_profile_interstitial_type': '1',
      'include_blocking': '1',
      'include_blocked_by': '1',
      'include_followed_by': '1',
      'include_want_retweets': '1',
      'include_mute_edge': '1',
      'include_can_dm': '1',
      'include_can_media_tag': '1',
      'skip_status': '1',
      'cards_platform': 'Web-12',
      'include_cards': '1',
      'include_composer_source': 'true',
      'include_ext_alt_text': 'true',
      'include_reply_count': '1',
      'tweet_mode': 'extended',
      'simple_quoted_tweet': 'true',
      'trim_user': 'false',
      'include_ext_media_color': 'true',
      'include_ext_media_availability': 'true',
      'auto_populate_reply_metadata': 'false',
      'batch_mode': 'off',
      'status': msg #new message
    }

    response = requests.post('https://api.twitter.com/1.1/statuses/update.json', headers=headers, data=data_post)

````
## Ao script:

- Já que sabemos como as request sao enviadas agora so precisamos recriar essas funcionalidades com uma linguagem da sua preferencia, toda vez que você faz alguma coisa no twitter ele envia um `update.json` onde esta alocado um comando que voce podera automatizar.

<center>
	<img src="image/img4.png"/>
	<img src="image/img5.png"/>
</center>

- Existe diversos site que você poderá converter o cURL pego do `update.json` para uma linguagem de programação da sua preferencia, no caso estou usando o site: `https://curl.trillworks.com/` que converte o cURL pego e converte em um script funcional em python

- Agora você so precisa fazer um script que mande os headers com seus parametros apontados para o endereço da api: `htps://api.twitter.com/1.1/statuses/update.json` fazendo assima emulação de um usuario normal

<center>
	<img src="image/img7.png"/>
</center>