# JQ handy helpers

### Testing them

find json online:

[This repo](https://github.com/LearnWebCode/json-example) > click on a JSON >  view Raw and curl the url.
ex: 
``` bash
curl https://raw.githubusercontent.com/LearnWebCode/json-example/master/pets-data.json
```
More complex ones:

Contentful example apps:

``` bash
curl 'https://cdn.contentful.com/spaces/wl1z0pal05vy/entries?content_type=2PqfXUJwE8qSYKuM0U6w8M&include=3' -H 'Accept: application/json, text/plain, */*' -H 'Referer: http://localhost:8080/equipe' -H 'Origin: http://localhost:8080' -H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_3) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.87 Safari/537.36' -H 'Authorization: Bearer 0e3ec801b5af550c8a1257e8623b1c77ac9b3d8fcfc1b2b7494e3cb77878f92a'
```


### Pipe it

```
curl https://raw.githubusercontent.com/LearnWebCode/json-example/master/pets-data.json | jq
```

## Cheat sheet

Using 
```
 curl https://raw.githubusercontent.com/LearnWebCode/json-example/master/pets-data.json
```
###  Get specific value in the json
```
jq '.pets[2].name'
```

###  get values using array iterator in the json
```
jq '.pets[].name'
```

### select only following a specific condition

``` bash
jq '.pets[] | select(.species=="Dog")'
```

### Restructure json 

```bash
jq '.pets[] | {title: .name, photoUrl: .photo}'
```


### List all attributes

``` bash
jq '[path(..)|map(if type=="number" then "[]" else tostring end)|join(".")|split(".[]")|join("[]")]|unique|map("."+.)|.[]'
```


## Resources:

[Doc](https://stedolan.github.io/jq/manual/)

[Cookbook](https://github.com/stedolan/jq/wiki/Cookbook)

[Trying it live](https://jqplay.org/)
