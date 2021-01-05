---
title: Onglet classe de la boîte de dialogue Propriétés de la fenêtre | Microsoft Docs
description: Sélectionnez l’onglet classe dans Visual Studio, déplacez le focus sur la fenêtre vue fenêtres, sélectionnez un nœud de fenêtre, puis choisissez afficher les propriétés de la > pour afficher la boîte de dialogue Propriétés de la fenêtre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3bf37d9e5d672f0ecce262699fdd5d704cde9efe
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729026"
---
# <a name="class-tab-window-properties-dialog-box"></a>Onglet Classe de la boîte de dialogue Propriétés de la fenêtre
Utilisez l’onglet **classe** pour afficher des informations sur la classe de la fenêtre sélectionnée. Pour afficher la [boîte de dialogue Propriétés](../debugger/window-properties-dialog-box.md)de la fenêtre, déplacez le focus vers la fenêtre [vue Windows](../debugger/windows-view.md) . Sélectionnez un nœud de fenêtre dans l’arborescence, puis choisissez **Propriétés** dans le menu **affichage** .

 Les paramètres suivants sont disponibles sous l’onglet **classe** :

|Entrée|Description|
|-----------|-----------------|
|**Nom de la classe**|Nom (ou numéro ordinal) de cette classe de fenêtre.|
|**Styles de la classe**|Combinaison de codes de style de classe.|
|**Octets de la classe**|Données spécifiques à l’application associées à cette classe de fenêtre.|
|**Classe Atom**|Atom pour la classe retournée par l’appel **registerClass** .|
|**Handle d’instance**|Handle d’instance du module qui a inscrit la classe. Les handles d’instance ne sont pas uniques.|
|**Octets de la fenêtre**|Nombre d’octets supplémentaires associés à chaque fenêtre de cette classe. La signification de ces octets est déterminée par l’application. Développez la zone de liste pour afficher les valeurs d’octets au format DWORD.|
|**Proc. de la fenêtre**|Adresse actuelle de la fonction **WndProc** pour les fenêtres de cette classe. Cela diffère de la **procédure de fenêtre** sous l’onglet **général** si la fenêtre est sous-classée.|
|**Nom de menu**|Nom du menu principal associé aux fenêtres de cette classe (« None » s’il n’y a aucun menu).|
|**Handle de l’icône**|Handle de l’icône associée aux fenêtres de cette classe ("none" s’il n’y a pas d’icône).|
|**Handle du curseur**|Handle du curseur associé aux fenêtres de cette classe ("none" s’il n’y a aucun curseur).|
|**Pinceau d’arrière-plan**|Handle pour le pinceau d’arrière-plan associé aux fenêtres de cette classe, ou l’une des couleurs prédéfinies COLOR_ * pour peindre l’arrière-plan de la fenêtre (« aucun » s’il n’y a aucun pinceau).|