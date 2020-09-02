---
title: Vue d’ensemble de la suppression de la source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651571"
---
# <a name="in-source-suppression-overview"></a>Vue d’ensemble de la suppression à la source
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La suppression dans la source est la possibilité de supprimer ou d’ignorer les violations de l’analyse du code dans le code managé en ajoutant l’attribut **SuppressMessage** aux segments de code qui provoquent les violations. L’attribut **SuppressMessage** est un attribut conditionnel qui est inclus dans les métadonnées il de votre assembly de code managé uniquement si le CODE_ANALYSIS symbole de compilation est défini au moment de la compilation.

 Dans C++/CLI, utilisez les macros CA_SUPPRESS_MESSAGE ou CA_GLOBAL_SUPPRESS_MESSAGE dans le fichier d’en-tête, pour ajouter l’attribut.

 Vous ne devez pas utiliser de suppressions dans la source sur les versions release pour empêcher l’expédition accidentelle des métadonnées de suppression dans la source. En raison du coût de traitement de la suppression en source, les performances de votre application peuvent également être dégradées en incluant les métadonnées de suppression dans la source.

> [!NOTE]
> Vous n’avez pas à coder manuellement ces attributs. Pour plus d’informations, consultez [Comment : supprimer des avertissements à l’aide de l’élément de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). L’élément de menu n’est pas disponible pour le code C++.

## <a name="suppressmessage-attribute"></a>SuppressMessage (attribut)
 Quand vous cliquez avec le bouton droit sur un avertissement d’analyse du code dans le **liste d’erreurs** puis que vous cliquez sur **supprimer le ou les messages**, un attribut **SuppressMessage** est ajouté dans votre code ou dans le fichier de suppression globale du projet.

 L’attribut **SuppressMessage** a le format suivant :

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]

```

 [C++]

```
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")

```

 Où :

- **Catégorie de règle** -catégorie dans laquelle la règle est définie. Pour plus d’informations sur les catégories de règle d’analyse du code, consultez [analyse du code pour les avertissements de code managé](../code-quality/code-analysis-for-managed-code-warnings.md).

- **ID de règle** : identificateur de la règle. La prise en charge comprend un nom abrégé et un nom long pour l’identificateur de règle. Le nom abrégé est CAXXXX ; le nom long est CAXXXX : FriendlyTypeName.

- **Justification** : texte utilisé pour documenter la raison de la suppression du message.

- **ID de message** : identificateur unique d’un problème pour chaque message.

- **Scope** : cible sur laquelle l’avertissement est supprimé. Si la cible n’est pas spécifiée, elle est définie sur la cible de l’attribut. Les étendues prises en charge sont les suivantes :

  - Module

  - Espace de noms

  - Ressource

  - Type

  - Membre

- **Cible** : identificateur utilisé pour spécifier la cible sur laquelle l’avertissement doit être supprimé. Il doit contenir un nom d’élément qualifié complet.

## <a name="suppressmessage-usage"></a>Utilisation de SuppressMessage
 Les avertissements d’analyse du code sont supprimés au niveau auquel une instance de l’attribut **SuppressMessage** est appliquée. L’objectif est de coupler étroitement les informations de suppression au code où la violation se produit.

 La forme générale de suppression inclut la catégorie de règle et un identificateur de règle qui contient une représentation facultative explicite du nom de la règle. Par exemple,

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 S’il existe des raisons de performances strictes pour réduire les métadonnées de suppression dans la source, le nom de la règle lui-même peut être omis. La catégorie de règle et son ID de règle constituent ensemble un identificateur de règle suffisamment unique. Par exemple,

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 Ce format n’est pas recommandé en raison de problèmes de maintenance.

## <a name="suppressing-multiple-violations-within-a-method-body"></a>Suppression de plusieurs violations dans un corps de méthode
 Les attributs ne peuvent être appliqués qu’à une méthode et ne peuvent pas être incorporés dans le corps de la méthode. Toutefois, vous pouvez spécifier l’identificateur comme ID de message pour distinguer plusieurs occurrences d’une violation au sein d’une méthode.

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>Code généré
 Les compilateurs de code managé et certains outils tiers génèrent du code pour faciliter le développement rapide de code. Le code généré par le compilateur qui apparaît dans les fichiers sources est généralement marqué avec l’attribut **GeneratedCodeAttribute** .

 Vous pouvez choisir de supprimer les avertissements et les erreurs d’analyse du code pour le code généré. Pour plus d’informations sur la façon de supprimer de tels avertissements et erreurs, consultez [Comment : supprimer des avertissements pour le code généré](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

 Notez que l’analyse du code ignore **GeneratedCodeAttribute** lorsqu’elle est appliquée à un assembly entier ou à un paramètre unique. Ces situations se produisent rarement.

## <a name="global-level-suppressions"></a>Suppressions au niveau global
 L’outil d’analyse du code managé examine les attributs **SuppressMessage** appliqués au niveau de l’assembly, du module, du type, du membre ou du paramètre. Il déclenche également des violations sur les ressources et les espaces de noms. Ces violations doivent être appliquées au niveau global et sont étendues et ciblées. Par exemple, le message suivant supprime une violation d’espace de noms :

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Quand vous supprimez un avertissement avec la portée espace de noms, il supprime l’avertissement par rapport à l’espace de noms lui-même. Elle ne supprime pas l’avertissement par rapport aux types dans l’espace de noms.

 Toute suppression peut être exprimée en spécifiant une portée explicite. Ces suppressions doivent résider au niveau global. Vous ne pouvez pas spécifier la suppression au niveau du membre en décorant un type.

 Les suppressions au niveau global sont le seul moyen de supprimer des messages qui font référence au code généré par le compilateur qui n’est pas mappé à une source utilisateur fournie explicitement. Par exemple, le code suivant supprime une violation par rapport à un constructeur émis par le compilateur :

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> La cible contient toujours le nom complet de l’élément.

## <a name="global-suppression-file"></a>Fichier de suppression globale
 Le fichier de suppression globale conserve les suppressions qui sont des suppressions au niveau global ou des suppressions qui ne spécifient pas de cible. Par exemple, les suppressions pour les violations au niveau de l’assembly sont stockées dans ce fichier. En outre, certaines suppressions de ASP.NET sont stockées dans ce fichier, car les paramètres de niveau projet ne sont pas disponibles pour le code-behind d’un formulaire. Une suppression globale est créée et ajoutée à votre projet la première fois que vous sélectionnez l’option **dans le fichier de suppression du projet** de la commande supprimer les **messages** dans la fenêtre de liste d’erreurs. Pour plus d’informations, consultez [Comment : supprimer des avertissements à l’aide de l’élément de menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).

## <a name="see-also"></a>Voir aussi
 <xref:System.Diagnostics.CodeAnalysis>
