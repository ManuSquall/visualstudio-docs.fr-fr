---
title: Vue d’ensemble de la Suppression Source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b7f0b3ef2b680dbe4675ef6e8875ef30a1f210bc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952758"
---
# <a name="in-source-suppression-overview"></a>Vue d’ensemble de la suppression à la source
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Suppression à la source est la possibilité de supprimer ou d’ignorer des violations d’analyse du Code dans le code managé en ajoutant la **SuppressMessage** les segments de code qui provoquent les violations de l’attribut. Le **SuppressMessage** attribut est un attribut conditionnel qui est inclus dans les métadonnées de langage intermédiaire de votre assembly de code managé uniquement si le symbole de compilation CODE_ANALYSIS est défini au moment de la compilation.  
  
 En C / c++ / CLI, utilisez les macros CA_SUPPRESS_MESSAGE ou CA_GLOBAL_SUPPRESS_MESSAGE dans le fichier d’en-tête, pour ajouter l’attribut.  
  
 Vous ne devez pas utiliser les suppressions dans la source sur les versions release pour empêcher les métadonnées de suppression à la source de livraison par inadvertance. En raison du coût de traitement de la suppression à la source, les performances de votre application peuvent également être réduites en incluant les métadonnées de suppression à la source.  
  
> [!NOTE]
>  Il est inutile pour transmettre code ces attributs vous-même. Pour plus d'informations, voir [Procédure : Supprimer les avertissements à l’aide de l’élément de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). L’élément de menu n’est pas disponible pour le code C++.  
  
## <a name="suppressmessage-attribute"></a>Attribut SuppressMessage  
 Lorsque vous cliquez sur un avertissement d’analyse du Code dans le **liste d’erreurs** puis cliquez sur **supprimer les messages**, un **SuppressMessage** attribut est ajouté dans votre code ou à la fichier de suppressions globales du projet.  
  
 Le **SuppressMessage** attribut a le format suivant :  
  
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
  
-   **Catégorie de règle** -catégorie dans laquelle la règle est définie. Pour plus d’informations sur les catégories de règles code analysis, consultez [analyse du Code pour les avertissements de Code géré](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Id de règle** -l’identificateur de la règle. Prise en charge inclut à la fois un nom court et long pour l’identificateur de règle. Le nom court est CAXXXX ; le nom long est CAXXXX:FriendlyTypeName.  
  
-   **Justification** -le texte qui est utilisé pour documenter la raison de la suppression du message.  
  
-   **Id de message** -identificateur Unique d’un problème pour chaque message.  
  
-   **Étendue** -la cible sur laquelle l’avertissement est supprimé. Si la cible n’est pas spécifiée, il est défini sur la cible de l’attribut. Étendues prises en charge sont les suivantes :  
  
    -   Module  
  
    -   Espace de noms  
  
    -   Ressource  
  
    -   Type  
  
    -   Membre  
  
-   **Cible** : un identificateur qui est utilisé pour spécifier la cible sur laquelle l’avertissement est supprimé. Il doit contenir un nom d’élément qualifié complet.  
  
## <a name="suppressmessage-usage"></a>Utilisation de SuppressMessage  
 Avertissements d’analyse du code sont supprimées au niveau auquel une instance de la **SuppressMessage** attribut est appliqué. Cela vise à coupler étroitement les informations de suppression pour le code où la violation se produit.  
  
 La forme générale de la suppression inclut la catégorie de règle et un identificateur de règle qui contient une représentation explicite facultative du nom de règle. Par exemple :  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 S’il existe des raisons de performances strict pour réduire les métadonnées de suppression à la source, le nom de la règle peut être omis. La catégorie de règle et son ID de règle constituent un identificateur de règle unique suffisant. Par exemple :  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Ce format n’est pas recommandé en raison de problèmes de facilité de maintenance.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Suppression de plusieurs Violations dans un corps de méthode  
 Les attributs peuvent uniquement être appliqués à une méthode et ne peut pas être incorporés dans le corps de méthode. Toutefois, vous pouvez spécifier l’identificateur comme ID de message pour distinguer plusieurs occurrences d’une violation dans une méthode.  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>Code généré  
 Les compilateurs de code managé et certains des outils tiers génèrent du code pour faciliter le développement de code rapide. Code généré par le compilateur qui s’affiche dans les fichiers sources est généralement signalé par le **GeneratedCodeAttribute** attribut.  
  
 Vous pouvez choisir s’il faut supprimer les avertissements d’analyse du Code et les erreurs pour le code généré. Pour plus d’informations sur la suppression de ces erreurs et avertissements, consultez [Comment : Supprimer les avertissements pour du Code généré](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Notez que l’analyse du Code ignore **GeneratedCodeAttribute** lorsqu’il est appliqué à un assembly entier ou un paramètre unique. Ces situations se produisent rarement.  
  
## <a name="global-level-suppressions"></a>Niveau global  
 L’outil d’analyse du code managé examine **SuppressMessage** attributs qui sont appliqués au niveau de l’assembly, module, type, membre ou paramètre. Il déclenche également des violations pour les ressources et les espaces de noms. Ces violations doivent être appliquées au niveau global et portent et ciblées. Par exemple, le message suivant supprime une violation de l’espace de noms :  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Lorsque vous supprimez un avertissement avec la portée espace de noms, il supprime l’avertissement par rapport à l’espace de noms. Il ne supprime pas l’avertissement par rapport aux types dans l’espace de noms.  
  
 Toute suppression peut être exprimée en spécifiant une portée explicite. Ces suppressions doivent exister au niveau global. Vous ne pouvez pas spécifier de suppression au niveau membre en décorant un type.  
  
 Les suppressions au niveau global sont la seule façon de supprimer les messages qui font référence au code généré par le compilateur qui ne mappe pas à la source de l’utilisateur fourni explicitement. Par exemple, le code suivant supprime une violation par rapport à un constructeur émis par un compilateur :  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Cible contient toujours le nom d’élément qualifié complet.  
  
## <a name="global-suppression-file"></a>Fichier de Suppression globale  
 Le fichier de suppression globale conserve les suppressions qui sont des suppressions au niveau global ou suppressions qui ne spécifient pas une cible. Par exemple, les suppressions de violations de niveau assembly sont stockées dans ce fichier. En outre, certaines suppressions ASP.NET sont stockées dans ce fichier, car les paramètres de niveau de projet ne sont pas disponibles pour le code-behind d’un formulaire. Une suppression globale est créée et ajoutée à votre projet la première fois que vous sélectionnez le **dans le fichier de Suppression de projet** possibilité du **supprimer les messages** commande dans la fenêtre liste d’erreurs. Pour plus d'informations, voir [Procédure : Supprimer les avertissements à l’aide de l’élément de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.CodeAnalysis>
