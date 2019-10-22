---
title: 'Comment : activer et désactiver la pluralisation (Concepteur O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665933"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Guide pratique pour activer et désactiver la pluralisation (Concepteur O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Par défaut, lorsque vous faites glisser des objets de base de données dont le nom se termine par un ou plusieurs **Explorateur de serveurs** /**Explorateur de base de données** sur les [outils de LINQ to SQL dans Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), les noms des classes d’entité générées sont modifiés du pluriel au au singulier. C'est pour insister sur le fait que la classe d'entité instanciée mappe à un enregistrement unique de données. Par exemple, l'ajout d'une table Customers au [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] génère une classe d'entité nommée Customer parce que la classe gérera les données d'un seul client.

> [!NOTE]
> Par défaut, la pluralisation est activée uniquement dans la version de langue anglaise de Visual Studio.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Pour activer et désactiver la pluralisation

1. Dans le menu **Outils** , cliquez sur **Options**.

2. Dans la boîte de dialogue **Options**, développez **Outils de base de données**.

> [!NOTE]
> Sélectionnez **Afficher tous les paramètres** si le nœud **Outils de base de données** n’est pas visible.

1. Cliquez sur **Concepteur O/R**.

2. Définissez la **pluralisation des noms** sur **activé**  = **false** pour définir le [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] afin qu’il ne modifie pas les noms de classe.

3. Définissez la **pluralisation des noms** sur **activé**  = **true** pour appliquer des règles de pluralité aux noms de classes des objets ajoutés au [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="see-also"></a>Voir aussi
 [Outils de LINQ to SQL dans Visual studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
