Django REST API
Nina Zakharenko


Serializers can be thought of as Django Forms

Validators - No configuration just a naming convention ...
```
def validate_text(self, attrs, source):
    value = attrs[source]
    if len(value) < 5:
        raise serializers(
        ...
```

Permissions:
    built in:
        `IsAuthenticated`
        `IsAdmin`

ModelViewSets
```
class TweetViewSet(viewsets.ModelViewSet):
    queryset = Tweet.objects.all()
    serializer_class = TweetSerializer
    permission_classes = (permissions.IsAuthenticated
    ...
```

Generic Views
APIView - Takes care of routing

Responses are unrendered
```
serializer = TweetSerializer(tweets, many=True)
return Response(serializer
...
```

ViewSet Routing
```
router = DefaultRouter()
router.register(r'tweets', views.TweetViewSet)
router.register(r'users', views.UserViewSets)
urlpatterns = patterns('', url(r'api/', include(router.urls))
```

Browsable API
- One of the strongest features of Django REST Framework
- Explore the API through a browser

Unit Testing
```
def test_create_invalid_tweet(self):
    self.client = APIClient()
    self.client.login(username="bob", password="bob")
    url = reverse('tweet-list')
    data = {"text": "x" } // fake data to post
    response = self.client.post(url, data, format='json')
    error_msg = response.data[text][0]
    assert
    ...
```

DRF 3.0
New Seralizers?

Install:
```
pip install djangorestframework
```

Documentation:
- Great documentation
http://www.django-rest-framework.org/

