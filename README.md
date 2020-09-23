# TIL
> 📝 Today I Learned

A collection of concise write-ups on small things I learn day to day across a variety of languages and technologies.

## A11Y

- Enable in browser spellchecking via bookmark

```javascript
javascript:document.body.contentEditable='true';document.body.spellcheck='true';void%200
```
[source](https://developer.paciellogroup.com/blog/2017/02/in-browser-spellchecking/)

## Cronjobs
- Run brew update every monday at 11 am
```bash
0 11 * * 1 /usr/local/bin/brew update && /usr/local/bin/brew upgrade
```

## Git

- Use git move to inform git about a case change of a file
```bash
$ git mv it.json IT.json
```

- Get every ticket number (commit message should be in the format `[#12345] Add foo`) of a period of time
```bash
$ git log --after 2018-03-26 | egrep -o '\[#\d*\]' | sort | uniq
```

- Get every ticket number __and commit message__ (commit message should be in the format `[#12345] Add foo`) of a period of time
```bash
$ git log --after 2016-07-15 | egrep -o '\[#\d*\](.*)' | sort | uniq
```

## Mac

- By default, Mac saves all screenshots to the desktop. If you'd like screenshots to be dumped somewhere else, you have to configure it manually from the command line with
```bash
$ defaults write com.apple.screencapture location ~/Downloads
$ killall SystemUIServer
```

## MySQL
- You can run the following command to get a list of the databases on your server and the size in GB they are consuming:
```sql
SELECT table_schema "Databases", sum( data_length + index_length ) / 1024 / 1024 / 1024 "Size (GB)" FROM information_schema.TABLES GROUP BY table_schema;
```

## Regex

- To anonymize files this regex replaces the full name with the initials of the person

```bash
#find expression
(\w{1}).*\.(\w{1}).*

#text
Test.Nutzer

#replace expression
$1.$2

#result
T.N
```

## JS
- To read article of local journalism parse the content and display text

```javascript
const demandForPayment = document.querySelector('.pdb-article-paidcontent-registration');
if(demandForPayment) {
    demandForPayment.remove();
}
const article = document.querySelector(".pdb-article script[type='application/ld+json']");
if(article) {
    const articleContent = JSON.parse(article.textContent);
    const scrambledArticleText = document.querySelector(".pdb-article-body");
    if(scrambledArticleText) {
        scrambledArticleText.innerText = articleContent.articleBody;
    }
}
```
