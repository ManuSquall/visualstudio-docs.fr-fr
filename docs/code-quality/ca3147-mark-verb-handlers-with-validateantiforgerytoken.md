---
title: 'CA3147 : Marquer les gestionnaires de verbe avec ValidateAntiForgeryToken'
ms.date: 08/08/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4b4369cfd310be9322d17b8bdbfe79880f2aa579
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008695"
---
# <a name="ca3147-mark-verb-handlers-with-validateantiforgerytoken"></a>CA3147 : Marquer les gestionnaires de verbe avec ValidateAntiForgeryToken

|||
|-|-|
|TypeName|MarkVerbHandlersWithValidateAntiForgeryToken|
|CheckId|CA3147|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode d’action de contrôleur ASP.NET MVC n’est pas marquée avec <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute?displayProperty=fullName>, ou d’un attribut en spécifiant le verbe HTTP, tel que <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute?displayProperty=fullName> ou <xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle

Lorsque vous concevez un contrôleur ASP.NET MVC, tenez compte des attaques par falsification de requête intersites. Une attaque de falsification de requête intersites peut envoyer des requêtes malveillantes à partir d’un utilisateur authentifié à votre contrôleur ASP.NET MVC. Pour plus d’informations, consultez [prévention de XSRF/CSRF dans ASP.NET MVC et web pages](/aspnet/mvc/overview/security/xsrfcsrf-prevention-in-aspnet-mvc-and-web-pages).

Cette règle vérifie ce contrôleur ASP.NET MVC méthodes d’action soit :

- Avoir le <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> et spécifier les verbes HTTP autorisés, non compris HTTP GET.

- Spécifiez la commande HTTP GET comme un verbe autorisé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

- Pour les actions de contrôleur ASP.NET MVC qui gèrent les demandes HTTP GET et n’ont pas les effets potentiellement dangereux, ajoutez un <xref:Microsoft.AspNetCore.Mvc.HttpGetAttribute> à la méthode.

   Si vous avez un ASP.NET MVC action du contrôleur qui gère HTTP GET demande et a des effets secondaires potentiellement dangereuses telles que la modification des données sensibles, votre application est vulnérable aux attaques par falsification de requête intersites.  Vous aurez besoin de reconcevoir votre application afin que seules les requêtes HTTP POST, PUT ou DELETE effectuer des opérations sensibles.

- Pour les actions de contrôleur ASP.NET MVC qui gèrent HTTP POST, PUT ou les demandes de suppression, ajoutez <xref:Microsoft.AspNetCore.Mvc.ValidateAntiForgeryTokenAttribute> et attributs qui spécifient les verbes HTTP autorisés (<xref:Microsoft.AspNetCore.Mvc.AcceptVerbsAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPostAttribute>, <xref:Microsoft.AspNetCore.Mvc.HttpPutAttribute>, ou <xref:Microsoft.AspNetCore.Mvc.HttpDeleteAttribute>). En outre, vous devez appeler <xref:Microsoft.AspNetCore.Mvc.ViewFeatures.HtmlHelper.AntiForgeryToken%2A?displayProperty=nameWithType> à partir de votre vue MVC ou de la page web de Razor. Pour obtenir un exemple, consultez [examen des méthodes de modification et de modifier la vue](/aspnet/mvc/overview/getting-started/introduction/examining-the-edit-methods-and-edit-view).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si :

- L’action du contrôleur ASP.NET MVC n’a aucun effets nuisibles.

- L’application valide le jeton anti-contrefaçon d’une manière différente.

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
