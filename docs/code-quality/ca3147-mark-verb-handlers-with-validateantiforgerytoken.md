---
title: 'CA3147 : Marquer les gestionnaires de verbe avec ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 01b290a4e4656aef079b27ce3abb2a66d7adeb75
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236986"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147 : Marquer les gestionnaires de verbe avec ValidateAntiForgeryToken

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode d’action du contrôleur MVC ASP.NET n’est pas marquée avec [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/dd492108(v=vs.118)), ou un attribut qui spécifie le verbe http, tel que [HttpGetAttribute](/previous-versions/aspnet/ee470993(v%3dvs.118)) ou [AcceptVerbsAttribute](/previous-versions/aspnet/dd470553%28v%3dvs.118%29).

## <a name="rule-description"></a>Description de la règle

Lors de la conception d’un contrôleur MVC ASP.NET, soyez attentif aux attaques de falsification de requête intersites. Une attaque de falsification de requête intersite peut envoyer des demandes malveillantes d’un utilisateur authentifié à votre contrôleur ASP.NET MVC. Pour plus d’informations, consultez [prévention de XSRF/CSRF dans ASP.NET MVC et pages Web](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Cette règle vérifie que les méthodes d’action du contrôleur ASP.NET MVC sont les suivantes :

- Avoir le [ValidateAntiforgeryTokenAttribute](/previous-versions/aspnet/dd492108%28v%3dvs.118%29) et spécifier les verbes HTTP autorisés, à l’exclusion de http.

- Spécifiez HTTP en tant que verbe autorisé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Pour les actions du contrôleur ASP.NET MVC qui gèrent les demandes HTTP et qui n’ont pas d’effets secondaires potentiellement dangereux, ajoutez un [HttpGetAttribute](/previous-versions/aspnet/ee470993%28v%3dvs.118%29) à la méthode.

   Si vous avez une action de contrôleur ASP.NET MVC qui gère les requêtes HTTP et présente des effets secondaires potentiellement dangereux tels que la modification des données sensibles, votre application est vulnérable aux attaques par falsification de requête intersites.  Vous devez reconcevoir votre application afin que seules les demandes HTTP, PUT ou DELETE effectuent des opérations sensibles.

- Pour les actions du contrôleur ASP.NET MVC qui gèrent les demandes HTTP, PUT ou DELETE, ajoutez des [ValidateAntiForgeryTokenAttribute](/previous-versions/aspnet/dd492108(v=vs.118)) et des attributs qui spécifient les verbes HTTP autorisés ([AcceptVerbsAttribute](/previous-versions/aspnet/dd470553%28v%3dvs.118%29), [HttpPostAttribute](/previous-versions/aspnet/ee264023%28v%3dvs.118%29), [ HttpPutAttribute](/previous-versions/aspnet/ee470909%28v%3dvs.118%29), ou [HttpDeleteAttribute](/previous-versions/aspnet/ee470917%28v%3dvs.118%29)). En outre, vous devez appeler la méthode [HtmlHelper. AntiForgeryToken ()](/previous-versions/aspnet/dd504812%28v%3dvs.118%29) à partir de votre vue MVC ou de votre page Web Razor. Pour obtenir un exemple, consultez [examen des méthodes de modification et de la vue Edit](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle dans les cas suivants :

- L’action du contrôleur ASP.NET MVC n’a aucun effet secondaire néfaste.

- L’application valide le jeton anti-contrefaçon d’une autre façon.

## <a name="validateantiforgerytoken-attribute-example"></a>Exemple d’attribut ValidateAntiForgeryToken

### <a name="violation"></a>Violation

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            // You don't want an attacker to specify to who and how much money to transfer.

            return null;
        }
    }
}
```

### <a name="solution"></a>Solution

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult TransferMoney(string toAccount, string amount)
        {
            return null;
        }
    }
}
```

## <a name="httpget-attribute-example"></a>Exemple d’attribut HttpGet

### <a name="violation"></a>Violation

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        public ActionResult Help(int topicId)
        {
            // This Help method is an example of a read-only operation with no harmful side effects.
            return null;
        }
    }
}
```

### <a name="solution"></a>Solution

```csharp
namespace TestNamespace
{
    using System.Web.Mvc;

    public class TestController : Controller
    {
        [HttpGet]
        public ActionResult Help(int topicId)
        {
            return null;
        }
    }
}
```
