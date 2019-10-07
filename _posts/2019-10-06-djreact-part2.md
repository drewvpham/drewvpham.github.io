---
title: "Django and React part 2!"
date: 2019-10-06
tags: [python, django, react]
header:
  #image: "/images/perceptron/percept.jpg"
excerpt: "a refresher on django and react pt 2!"
mathjax: "true"
---


Wow this was a great video that went into detail on Django REST framework's view classes and we get to see how easy it is to make api calls to our Django web application. The video discusses creating, updating and deleting data.

The video goes into detail on ModelViewSet. We are able to reduce all of this code:

```
from rest_framework.generics import ListAPIView, RetrieveAPIView, CreateAPIView, UpdateAPIView, DestroyAPIView



class ArticleListView(ListAPIView):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer


class ArticleDetailView(RetrieveAPIView):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer


class ArticleCreateView(CreateAPIView):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer


class ArticleUpdateView(UpdateAPIView):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer


class ArticleDeleteView(DestroyAPIView):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer

```
into this:
```

from articles.models import Article
from .serializers import ArticleSerializer
from rest_framework import viewsets


class ArticleViewSet(viewsets.ModelViewSet):
    queryset = Article.objects.all()
    serializer_class = ArticleSerializer
```
Amazing!!!! But! This method only works if you don't intend on customizing your views.

This is interesting because it can combine all the different types of views into just 1! Very clean and very simple.