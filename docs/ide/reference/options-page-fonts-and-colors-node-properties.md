---
title: Page Options, Polices et couleurs, propriétés de nœud
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cf39d9a01794e34a50d81489214bb006e4c6448
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944685"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Page Options, Polices et couleurs, propriétés de nœud
Ce document décrit les propriétés de police et de couleur d’une fenêtre Outil qui est inscrite pour apparaître sous **Polices et couleurs** dans la catégorie **Environnement** de la boîte de dialogue **Options**. La nature dynamique des groupes d’éléments colorables, qui peuvent changer si des packages VS sont installés ou désinstallés, est prise en charge.

 La section suivante montre un exemple de type de fenêtres inscrites et des propriétés qui sont disponibles pour chaque fenêtre.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Éditeur de texte ou imprimante ou boîtes de dialogue et fenêtres Outil
 `DTE.Properties("FontsAndColors", "TextEditor")`

 - ou -

 `DTE.Properties("FontsAndColors", "Printer")`

 - ou -

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nom de l'élément de propriété|Value|Description|
|------------------------|-----------|-----------------|
|FontFamily|Get/Set (chaîne)|Nom de la police à utiliser, tel que « Courier New ».|
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|Valeur <xref:EnvDTE.vsFontCharSet> indiquant le type de jeu de caractères à utiliser, tel que l’hébreu ou le russe.|
|FontSize|Get/Set (Short)|Taille de police à utiliser, en points. Par exemple, 10 ou 12.|

## <a name="see-also"></a>Voir aussi

- [Contrôle des paramètres de la boîte de dialogue Options](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Détermination des noms d’éléments de propriété dans les pages Options](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Page Options, Propriétés du nœud Environnement](../../ide/reference/options-page-environment-node-properties.md)
- [Page Options, Propriétés du nœud Éditeur de texte](../../ide/reference/options-page-text-editor-node-properties.md)