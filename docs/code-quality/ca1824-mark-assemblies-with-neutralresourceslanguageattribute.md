---
title: "CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6c9d4da3becaa6831f30a5cc6c72d1f0b3b70eea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|CheckId|CA1824|  
|Category|Microsoft.Performance|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un assembly contient un **ResX**-en fonction des ressources, mais n’a pas le <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> appliqué.  
  
## <a name="rule-description"></a>Description de la règle  
 Le **NeutralResourcesLanguage** attribut informe le **ResourceManager** de la langue utilisée pour afficher les ressources de la culture neutre d’un assembly. Lorsqu’il recherche des ressources dans la même culture que la langue des ressources neutres, le **ResourceManager** utilise automatiquement les ressources qui sont trouvent dans l’assembly principal. Pour cela, au lieu de rechercher un assembly satellite ayant la culture d’interface utilisateur actuelle du thread actuel. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail.  
  
## <a name="fixing-violations"></a>Résolution des Violations  
 Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly et spécifier la langue des ressources de la culture neutre.  
  
## <a name="specifying-the-language"></a>Spécification de la langue  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Pour spécifier la langue de la ressource de la culture neutre  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit de votre projet, puis cliquez sur **propriétés**.  
  
2.  Dans la barre de navigation de gauche, sélectionnez **Application**, puis cliquez sur **informations de l’Assembly**.  
  
3.  Dans le **informations d’Assembly** boîte de dialogue, sélectionnez la langue à partir de la **langage neutre** liste déroulante.  
  
4.  Cliquez sur **OK**.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle. Toutefois, peut réduire les performances de démarrage.