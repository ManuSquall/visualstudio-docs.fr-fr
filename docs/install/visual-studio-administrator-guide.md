---
title: "Guide de l’administrateur Visual Studio │ Microsoft Docs"
ms.custom: 
ms.date: 01/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5e1ab0284a11fb9ecf30694d22b8bb5dc7a52a6d
ms.openlocfilehash: 91fb897e0bf124234484c3aada08ac57c4be1923
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017-rc"></a>Guide de l’administrateur Visual Studio pour Visual Studio 2017 RC

Vous pouvez déployer Visual Studio sur un réseau dans la mesure où chaque ordinateur cible satisfait aux [conditions d’installation minimales](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Vous pouvez créer un partage réseau en exécutant le fichier d’installation avec le commutateur --layout (comme décrit dans la page [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)) et en le copiant de l’ordinateur local vers le partage réseau.   

 Notez que les installations effectuées à partir d’un partage réseau « se souviennent » de l’emplacement source dont elles sont issues. Cela signifie que la réparation d’un ordinateur client peut devoir retourner sur le partage réseau à partir duquel le client a été initialement installé. Choisissez soigneusement votre emplacement réseau : sa durée de vie doit être au moins aussi longue que celle des clients Visual Studio 2017 qui s’exécutent dans votre organisation.  

 > [!IMPORTANT]
 > Alors que Visual Studio 2017 RC est généralement pris en charge pour une utilisation dans un environnement de production, les charges de travail et les composants qui sont marqués « Préversion » dans l’interface utilisateur de l’installation ne le sont pas.

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio 2017 RC](install-visual-studio.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio 2017 RC](create-an-offline-installation-of-visual-studio.md)
* [Guide pratique pour signaler un problème avec Visual Studio 2017 RC](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

