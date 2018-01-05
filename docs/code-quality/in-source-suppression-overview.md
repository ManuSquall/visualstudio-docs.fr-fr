---
title: "Vue d’ensemble de la Suppression Source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 92babbf3c7a5863d178463b69525bdb722bf28ad
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="in-source-suppression-overview"></a>Vue d’ensemble de la suppression à la source
Suppression à la source est la possibilité de supprimer ou d’ignorer des violations d’analyse du Code dans le code managé en ajoutant la **SuppressMessage** les segments de code qui provoquent les violations de l’attribut. Le **SuppressMessage** attribut est un attribut conditionnel qui est inclus dans les métadonnées de langage intermédiaire de votre assembly de code managé uniquement si le symbole de compilation CODE_ANALYSIS est défini au moment de la compilation.  
  
 En langage c++ / CLI, utilisez les macros CA_SUPPRESS_MESSAGE ou CA_GLOBAL_SUPPRESS_MESSAGE dans le fichier d’en-tête pour ajouter l’attribut.  
  
 Vous ne devez pas utiliser les suppressions dans la source sur les versions release pour empêcher la copie les métadonnées de suppression à la source par inadvertance. En raison du coût de traitement de la suppression à la source, les performances de votre application peuvent également être dégradé en incluant les métadonnées de suppression à la source.  
  
> [!NOTE]
>  Il est inutile de rendre code ces attributs vous-même. Pour plus d’informations, consultez [Comment : supprimer les avertissements à l’aide de l’élément de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). L’élément de menu n’est pas disponible pour le code C++.  
  
## <a name="suppressmessage-attribute"></a>SuppressMessage (attribut)  
 Lorsque vous cliquez sur un avertissement d’analyse du Code dans le **liste d’erreurs** puis cliquez sur **supprimer les messages**, un **SuppressMessage** attribut est ajouté dans votre code ou à la fichier des suppressions globales du projet.  
  
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
  
-   **Catégorie de règle** -catégorie dans laquelle la règle est définie. Pour plus d’informations sur les catégories de règles analyse de code, consultez [l’analyse du Code pour les avertissements de Code managé](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Id de règle** -l’identificateur de la règle. Prise en charge inclut à la fois un nom court et long de l’identificateur de la règle. Le nom court est CAXXXX ; le nom long est CAXXXX:FriendlyTypeName.  
  
-   **Justification** -le texte qui est utilisé pour documenter la raison de la suppression du message.  
  
-   **Id de message** -identificateur Unique d’un problème pour chaque message.  
  
-   **Étendue** -cible sur laquelle l’avertissement est supprimé. Si la cible n’est pas spécifiée, il est défini à la cible de l’attribut. Les étendues prises en charge sont les suivantes :  
  
    -   Module  
  
    -   Espace de noms  
  
    -   Ressource  
  
    -   Type  
  
    -   Membre  
  
-   **Cible** - un identificateur qui est utilisé pour spécifier la cible sur laquelle l’avertissement est supprimé. Il doit contenir un nom d’élément complet.  
  
## <a name="suppressmessage-usage"></a>Utilisation de SuppressMessage  
 Avertissements d’analyse du code sont supprimés au niveau auquel une instance de la **SuppressMessage** attribut est appliqué. L’objectif de ce est étroitement coupler les informations sur la suppression du code où la violation se produit.  
  
 La forme générale de la suppression inclut la catégorie de règle et un identificateur de règle qui contient une représentation explicite facultative du nom de la règle. Par exemple :  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 S’il existe des raisons de performances strict pour réduire les métadonnées de suppression à la source, le nom de la règle peut être omis. La catégorie de règle et son ID de règle constituent un identificateur de règle unique suffisant. Par exemple :  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Ce format n’est pas recommandé en raison de problèmes de facilité de maintenance.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Suppression de plusieurs Violations dans un corps de méthode  
 Les attributs peuvent uniquement être appliqués à une méthode et ne peut pas être incorporés dans le corps de méthode. Toutefois, vous pouvez spécifier l’identificateur comme ID de message pour distinguer plusieurs occurrences d’une violation dans une méthode.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-csharp[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## <a name="generated-code"></a>Code généré  
 Les compilateurs de code managé et de certains des outils tiers génèrent du code pour faciliter le développement de code rapide. Code généré par le compilateur qui apparaît dans les fichiers sources est généralement signalé par le **GeneratedCodeAttribute** attribut.  
  
 Vous pouvez choisir s’il faut supprimer les avertissements d’analyse du Code et les erreurs pour le code généré. Pour plus d’informations sur la façon de supprimer ces avertissements et les erreurs, consultez [Comment : supprimer les avertissements pour du Code généré](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Notez que l’analyse du Code ignore **GeneratedCodeAttribute** lorsqu’il est appliqué à un assembly entier ou un paramètre unique. Ces situations se produisent rarement.  
  
## <a name="global-level-suppressions"></a>Suppressions au niveau global  
 L’outil d’analyse du code managé examine **SuppressMessage** attributs qui sont appliqués au niveau de l’assembly, module, type, membre ou paramètre. Il déclenche également des violations pour les ressources et les espaces de noms. Ces violations doivent être appliquées au niveau global d’une étendue et sont ciblées. Par exemple, le message suivant supprime une violation de l’espace de noms :  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Lorsque vous supprimez un avertissement avec la portée espace de noms, il supprime l’avertissement par rapport à l’espace de noms. Elle ne supprime pas l’avertissement par rapport aux types dans l’espace de noms.  
  
 Toute suppression peut être exprimée en spécifiant une portée explicite. Ces suppressions doivent exister au niveau global. Vous ne pouvez pas spécifier de suppression au niveau du membre en décorant un type.  
  
 Les suppressions au niveau global sont la seule façon de supprimer les messages qui font référence au code généré par le compilateur qui ne correspond pas à la source de l’utilisateur fournies explicitement. Par exemple, le code suivant supprime une violation sur un constructeur émis par le compilateur :  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Le serveur cible contient toujours le nom qualifié complet.  
  
## <a name="global-suppression-file"></a>Fichier de Suppression globale  
 Le fichier de suppression globale conserve les suppressions qui sont soit au niveau global ou qui ne spécifient pas une cible. Par exemple, les suppressions de violations de niveau assembly sont stockées dans ce fichier. En outre, certaines suppressions ASP.NET sont stockées dans ce fichier, car les paramètres de niveau de projet ne sont pas disponibles pour le code-behind d’un formulaire. Une suppression globale est créée et ajoutée à votre projet la première fois que vous sélectionnez le **dans le fichier de Suppression de projet** option de le **supprimer les messages** commande dans la fenêtre liste d’erreurs. Pour plus d’informations, consultez [Comment : supprimer les avertissements à l’aide de l’élément de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.CodeAnalysis>