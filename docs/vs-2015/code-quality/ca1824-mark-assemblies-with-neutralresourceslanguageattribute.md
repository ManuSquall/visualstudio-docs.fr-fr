---
title: 'CA1824 : Marquez les assemblys avec NeutralResourcesLanguageAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 13f635398ecab7c0bd9436a86a43a15d4908b163
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892595"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Category|Microsoft.Performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un assembly contient un **ResX**-en fonction des ressources, mais n’a pas le <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> appliqué.

## <a name="rule-description"></a>Description de la règle
 Le **NeutralResourcesLanguage** attribut informe le **ResourceManager** de la langue qui a été utilisée pour afficher les ressources de la culture neutre d’un assembly. Lorsqu’il recherche des ressources dans la même culture que le langage des ressources neutre, le **ResourceManager** utilise automatiquement les ressources qui sont trouvent dans l’assembly principal. Pour cela, au lieu de rechercher un assembly satellite ayant la culture d’interface utilisateur actuelle pour le thread actuel. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail.

## <a name="fixing-violations"></a>Résolution des Violations
 Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly et spécifier la langue des ressources de la culture neutre.

## <a name="specifying-the-language"></a>Spécification de la langue

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Pour spécifier la langue de la ressource de la culture neutre

1.  Dans **l’Explorateur de solutions**, cliquez sur votre projet, puis cliquez sur **propriétés**.

2.  Dans la barre de navigation de gauche, sélectionnez **Application**, puis cliquez sur **informations de l’Assembly**.

3.  Dans le **informations de l’Assembly** boîte de dialogue, sélectionnez la langue à partir de la **indépendant de la langue** liste déroulante.

4.  Cliquez sur **OK**.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est permis de supprimer un avertissement de cette règle. Toutefois, peut diminuer les performances de démarrage.



