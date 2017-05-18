---
title: "Mettre à jour une installation réseau de Visual Studio | Microsoft Docs"
description: "{{ESPACE RÉSERVÉ}}"
ms.date: 05/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
author: timsneath
ms.author: tims
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 75c65d75ab751058ac435d62f253ead149ccfe42
ms.contentlocale: fr-fr
ms.lasthandoff: 05/09/2017

---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Mettre à jour une installation réseau de Visual Studio

Il est possible de mettre à jour une disposition d’installation réseau de Visual Studio avec les dernières mises à jour de produit afin de pouvoir l’utiliser à la fois comme point d’installation de la dernière mise à jour de Visual Studio et aussi pour gérer les installations déjà déployées sur les stations de travail clientes.

## <a name="how-to-update-a-network-layout"></a>Comment mettre à jour une disposition réseau
Pour actualiser le partage d’installation réseau afin qu’il comprenne les dernières mises à jour, exécutez la même commande `--layout` que celle que vous avez exécutée lors de la création de la disposition pour télécharger progressivement les packages mis à jour.

Si vous avez sélectionné une disposition partielle quand vous avez créé la disposition réseau, vérifiez que vous utilisez les mêmes paramètres de ligne de commande que ceux que vous avez utilisés lors de la création de la disposition d’installation réseau (autrement dit, les mêmes charges de travail et langues). Si vous choisissez des options différentes, la deuxième commande `--layout` ne met pas à jour les packages qui n’ont pas été spécifiés la deuxième fois.

Si vous hébergez une disposition sur un partage de fichiers, il est recommandé de mettre à jour une copie privée de la disposition (par exemple, `c:\vs2017offline`) et, une fois que tout le contenu mis à jour est téléchargé, de la copier sur votre partage de fichiers (par exemple, `\\server\products\VS2017`).  Si vous ne le faites pas, il est très probable que les utilisateurs exécutant le programme d’installation pendant la mise à jour de la disposition ne pourront pas obtenir tout le contenu de la disposition, car il n’est pas totalement à jour.

## <a name="how-to-deploy-an-update-to-client-machines"></a>Comment déployer une mise à jour sur les ordinateurs clients
Selon la configuration de votre environnement réseau, une mise à jour peut être déployée par un administrateur d’entreprise ou lancée à partir d’un ordinateur client. 

- Les utilisateurs peuvent mettre à jour une instance de Visual Studio qui a été installée à partir d’un dossier d’installation hors connexion :
  - Exécutez le programme d’installation de Visual Studio.
  - Cliquez ensuite sur **Mettre à jour**.

- Les administrateurs peuvent mettre à jour les déploiements de clients de Visual Studio sans aucune intervention utilisateur avec deux commandes distinctes :
  - Mettez tout d’abord à jour le programme d’installation de Visual Studio : <br>```vs_enterprise.exe --quiet --update```
  - Mettez ensuite à jour l’application Visual Studio proprement dite : <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Utilisez la [commande vswhere.exe](tools-for-managing-visual-studio-instances.md) pour identifier le chemin d’installation d’une instance existante de Visual Studio sur un ordinateur client.

> [!TIP]
> Pour plus d’informations sur le contrôle du moment de la présentation des notifications de mise à jour aux utilisateurs, consultez [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md).


## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio](install-visual-studio.md)
* [Guide de l’administrateur Visual Studio](visual-studio-administrator-guide.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Outils de détection et de gestion des instances de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Contrôler les mises à jour applicables aux déploiements de Visual Studio à partir du réseau](controlling-updates-to-visual-studio-deployments.md)

