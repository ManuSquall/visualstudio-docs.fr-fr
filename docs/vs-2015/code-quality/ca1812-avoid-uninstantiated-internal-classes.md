---
title: 'CA1812 : Évitez les classes internes non instanciées | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 401fbfbccfeeeeec5cbdc0e791b110d1b5f0201b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543973"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812 : Évitez les classes internes non instanciées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly.

## <a name="rule-description"></a>Description de la règle
 Cette règle tente de localiser un appel à l’un des constructeurs du type et signale une violation si aucun appel n’est trouvé.

 Les types suivants ne sont pas examinés par cette règle :

- Types valeur

- Types abstraits

- Énumérations

- Délégués

- Types de tableau émis par le compilateur

- Types qui ne peuvent pas être instanciés et qui définissent `static` `Shared` uniquement les méthodes (dans Visual Basic).

  Si vous appliquez <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> à l’assembly en cours d’analyse, cette règle ne se produira pas sur les constructeurs marqués comme `internal` parce que vous ne pouvez pas déterminer si un champ est utilisé par un autre `friend` assembly.

  Même si vous ne pouvez pas contourner cette limitation dans l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] analyse du code, le FxCop externe autonome se produit sur les constructeurs internes si chaque `friend` assembly est présent dans l’analyse.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le type ou ajoutez le code qui l’utilise. Si le type contient uniquement des méthodes statiques, ajoutez l’un des éléments suivants au type pour empêcher le compilateur d’émettre un constructeur d’instance public par défaut :

- Constructeur privé pour les types qui ciblent les [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versions 1,0 et 1,1.

- `static` `Shared` Modificateur (en Visual Basic) pour les types qui ciblent [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle. Nous vous recommandons de supprimer cet avertissement dans les cas suivants :

- La classe est créée par le biais de méthodes de réflexion à liaison tardive, telles que <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> .

- La classe est créée automatiquement par le runtime ou [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Par exemple, les classes qui implémentent <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> ou <xref:System.Web.IHttpHandler?displayProperty=fullName> .

- La classe est passée en tant que paramètre de type générique qui a une nouvelle contrainte. Par exemple, l’exemple suivant génère cette règle.

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

  Dans ce cas, nous vous recommandons de supprimer cet avertissement.

## <a name="related-rules"></a>Règles associées
 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)
