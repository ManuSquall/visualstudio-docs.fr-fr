---
title: "Guide de l’administrateur Visual Studio │ Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 69ac1327fa9233bf0ecc18be5e7d2f2a4f82b3b0
ms.lasthandoff: 03/07/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Guide de l’administrateur Visual Studio pour Visual Studio 2017

Vous pouvez déployer Visual Studio sur un réseau dans la mesure où chaque ordinateur cible satisfait aux [conditions d’installation minimales](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Vous pouvez créer un partage réseau en exécutant le fichier d’installation avec le commutateur --layout (comme décrit dans la page [Créer une installation hors connexion de Visual Studio](create-an-offline-installation-of-visual-studio.md)) et en le copiant de l’ordinateur local vers le partage réseau.   

 Notez que les installations effectuées à partir d’un partage réseau « se souviennent » de l’emplacement source dont elles sont issues. Cela signifie que la réparation d’un ordinateur client peut devoir retourner sur le partage réseau à partir duquel le client a été initialement installé. Choisissez soigneusement votre emplacement réseau : sa durée de vie doit être au moins aussi longue que celle des clients Visual Studio 2017 qui s’exécutent dans votre organisation.

## <a name="tools"></a>Outils

 Nous proposons plusieurs outils pour vous aider à gérer vos installations de Visual Studio :

* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples) : exemples C# et C++ destiné à aider les utilisateurs à interroger les instances de Visual Studio sur leurs ordinateurs.
* [VSWhere](https://github.com/microsoft/vswhere) : un fichier .exe C++ qui vous aide à trouver principaux outils Visual Studio.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell) : scripts PowerShell performants pour les tâches d’administration courantes relatives à l’installation.


## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio 2017](install-visual-studio.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Créer une installation hors connexion de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Utiliser les ID de composant et de charge de travail Visual Studio pour personnaliser votre installation hors connexion](workload-and-component-ids.md)
* [Signaler un problème avec Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

