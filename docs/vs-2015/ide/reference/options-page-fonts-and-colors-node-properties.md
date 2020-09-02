---
title: Page Options, Polices et couleurs, propriétés de nœud | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23aa4eff3339ad3cd3ab7d4106745dc6fa83df34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662428"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Page Options, Polices et couleurs, propriétés de nœud
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ce document décrit les propriétés de police et de couleur d’une fenêtre Outil qui est inscrite pour apparaître sous **Polices et couleurs** dans la catégorie **Environnement** de la boîte de dialogue **Options**. La nature dynamique des groupes d’éléments colorables, qui peuvent changer si des packages VS sont installés ou désinstallés, est prise en charge.

 La section suivante montre un exemple de type de fenêtres inscrites et des propriétés qui sont disponibles pour chaque fenêtre.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Éditeur de texte ou imprimante ou boîtes de dialogue et fenêtres Outil
 `DTE.Properties("FontsAndColors", "TextEditor")`

 - ou -

 `DTE.Properties("FontsAndColors", "Printer")`

 - ou -

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nom de l'élément de propriété|Valeur|Description|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set (chaîne)|Nom de la police à utiliser, tel que « Courier New ».|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Valeur <xref:EnvDTE.vsFontCharSet> indiquant le type de jeu de caractères à utiliser, tel que l’hébreu ou le russe.|
|FontSize|Get/Set (Short)|Taille de police à utiliser, en points. Par exemple, 10 ou 12.|

## <a name="see-also"></a>Voir aussi
 [Contrôle des options paramètres](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [détermination des noms des éléments de propriété dans options pages](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) options [page, propriétés du nœud environnement](../../ide/reference/options-page-environment-node-properties.md) [page Options, éditeur de texte Propriétés du nœud](../../ide/reference/options-page-text-editor-node-properties.md)
