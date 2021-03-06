# Go-Stanford-NLP

[![License](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/kamildrazkiewicz/go-stanford-nlp/blob/master/LICENSE) [![GoDoc](http://godoc.org/github.com/kamildrazkiewicz/go-stanford-nlp?status.svg)](http://godoc.org/github.com/kamildrazkiewicz/go-stanford-nlp) [![GoReport](https://goreportcard.com/badge/github.com/kamildrazkiewicz/go-stanford-nlp)](https://goreportcard.com/report/github.com/kamildrazkiewicz/go-stanford-nlp) 
[![Build Status](https://travis-ci.org/kamildrazkiewicz/go-stanford-nlp.svg?branch=master)](https://travis-ci.org/kamildrazkiewicz/go-stanford-nlp)

Go wrapper for Stanford NLP Part-Of-Speech Tagger (GPLv2)

More info: http://nlp.stanford.edu/software/tagger.shtml


## Install

Install the package with:

```bash
go get github.com/kamildrazkiewicz/go-stanford-nlp
```

Import it with:

```go
import "github.com/kamildrazkiewicz/go-stanford-nlp"
```

and use `pos` as the package name inside the code.

## Example

```go
func main() {
	var (
		tagger *pos.Tagger
		res    []*pos.Result
		err    error
	)

	if tagger, err = pos.NewTagger(
		"ext/english-left3words-distsim.tagger",    // path to model
		"ext/stanford-postagger.jar"); err != nil { // path to jar tagger file
		fmt.Print(err)
		return
	}
	if res, err = tagger.Tag("What is your name?"); err != nil {
		fmt.Print(err)
		return
	}
	for _, r := range res {
		fmt.Println(r.Word, r.TAG, r.Description())
	}

}
```

Output will be:
```
What WP Wh-pronoun
is VBZ Verb, 3rd person singular present
your PRP$ Possessive pronoun
name NN Noun, singular or mass
? .
```
