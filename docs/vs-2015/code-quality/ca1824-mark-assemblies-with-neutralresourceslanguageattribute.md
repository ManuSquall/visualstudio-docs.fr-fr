---
title: 'CA1824 : marquer les assemblys avec NeutralResourcesLanguageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19077a63d5aa22bda3f968943703a82488e2745d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545286"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Un assembly contient une ressource **resx**, mais ne lui est pas <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> appliquée.

## <a name="rule-description"></a>Description de la règle
 L’attribut **NeutralResourcesLanguage** informe le **ResourceManager** de la langue utilisée pour afficher les ressources de la culture neutre d’un assembly. Lorsqu’il recherche des ressources dans la même culture que la langue des ressources neutres, le **ResourceManager** utilise automatiquement les ressources qui se trouvent dans l’assembly principal. Au lieu de rechercher un assembly satellite qui a la culture d’interface utilisateur actuelle pour le thread actuel. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail.

## <a name="fixing-violations"></a>Correction des violations
 Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly et spécifiez la langue des ressources de la culture neutre.

## <a name="specifying-the-language"></a>Spécification de la langue

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Pour spécifier la langue de la ressource de la culture neutre

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis cliquez sur **Propriétés**.

2. Dans la barre de navigation de gauche, sélectionnez **application**, puis cliquez sur informations de l' **assembly**.

3. Dans la boîte de dialogue informations de l' **assembly** , sélectionnez la langue dans la liste déroulante **langue neutre** .

4. Cliquez sur **OK**.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est permis de supprimer un avertissement de cette règle. Toutefois, les performances de démarrage peuvent diminuer.
