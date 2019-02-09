---
title: 'CA1812 : Évitez les classes internes non instanciées'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08d8b907e4a211b0735f07377c21dec1c0a982c9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950745"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812 : Évitez les classes internes non instanciées

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly.

## <a name="rule-description"></a>Description de la règle

Cette règle tente de localiser un appel à un des constructeurs du type et signale une violation si aucun appel n’est trouvé.

Les types suivants ne sont pas examinés par cette règle :

- Types de valeur

- Types abstraits

- Énumérations

- Délégués

- Types de tableau émis par le compilateur

- Les types qui ne peut pas être instanciée et qui définissent `static` (`Shared` en Visual Basic) uniquement les méthodes.

Si vous appliquez <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> à l’assembly qui est en cours d’analyse, cette règle se produira pas sur les constructeurs portent la mention `internal` parce que vous ne pouvez pas savoir si un champ est utilisé par un autre `friend` assembly.

Même si vous ne pouvez pas contourner cette limitation dans Visual Studio Code Analysis, l’outil FxCop autonome externe se produit sur les constructeurs internes si chaque `friend` assembly est présent dans l’analyse.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le type ou ajoutez le code qui l’utilise. Si le type contient uniquement des méthodes statiques, ajoutez une des opérations suivantes pour le type pour empêcher le compilateur d’émettre un constructeur d’instance public par défaut :

- Un constructeur privé pour les types qui ciblent des versions 1.0 et 1.1 du .NET Framework.

- Le `static` (`Shared` en Visual Basic) qui ciblent des types de modificateur pour [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle. Nous vous recommandons de supprimer cet avertissement dans les situations suivantes :

- La classe est créée par le biais des méthodes de la réflexion à liaison tardive comme <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- La classe est créée automatiquement par le runtime ou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Par exemple, les classes qui implémentent <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> ou <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- La classe est passée comme un paramètre de type générique qui a une nouvelle contrainte. Par exemple, l’exemple suivant génère cette règle.

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }
    // [...]
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

  Dans ces situations, nous vous recommandons de que vous supprimer cet avertissement.

## <a name="related-rules"></a>Règles associées

[CA1811 : Évitez le recours à code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)

[CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)