---
title: "Guide de l’administrateur Visual Studio │ Microsoft Docs"
ms.custom: 
ms.date: 04/06/2017
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
ms.sourcegitcommit: 47c39bd711b69efdb863d71f11e3e472054a3ce3
ms.openlocfilehash: aebd3abc671f997773fc7c557627ca23b9bf82bd
ms.lasthandoff: 04/06/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Guide de l’administrateur Visual Studio pour Visual Studio 2017

 Vous pouvez déployer Visual Studio sur un réseau dans la mesure où chaque ordinateur cible satisfait aux [conditions d’installation minimales](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs).

 Que votre déploiement s’effectue à l’aide de logiciels comme System Center ou à l’aide d’un fichier de commandes, vous voulez généralement effectuer les étapes suivantes :

1. [Mettre en cache la disposition du produit Visual Studio](create-an-offline-installation-of-visual-studio.md) dans un emplacement réseau.

2. [Sélectionner les charges de travail et les composants](workload-and-component-ids.md) à installer.

3. [Générer un script d’installation](use-command-line-parameters-to-install-visual-studio.md) à l’aide des éléments sélectionnés et d’autres paramètres de ligne de commande pour contrôler l’installation.

4. Éventuellement, [appliquer une clé de produit de licence en volume](automatically-apply-product-keys-when-deploying-visual-studio.md) dans le cadre du script d’installation afin que les utilisateurs n’aient pas à activer le logiciel séparément.

5. Utilisez la technologie de déploiement de votre choix pour exécuter le script généré dans les étapes précédentes sur vos stations de travail de développement cibles.

6. Actualiser votre emplacement réseau avec les dernières mises à jour de Visual Studio en exécutant régulièrement la commande utilisée à l’étape 1 pour ajouter des composants mis à jour.

> [!IMPORTANT]
>  Notez que les installations effectuées à partir d’un partage réseau « se souviennent » de l’emplacement source dont elles sont issues. Cela signifie que la réparation d’un ordinateur client peut devoir retourner sur le partage réseau à partir duquel le client a été initialement installé. Choisissez soigneusement votre emplacement réseau : sa durée de vie doit être au moins aussi longue que celle des clients Visual Studio 2017 qui s’exécutent dans votre organisation.

## <a name="tools"></a>Outils

 Nous avons mis à disposition plusieurs outils qui vous aideront à détecter et à gérer les instances de Visual Studio installées sur les ordinateurs clients :

* [VSWhere](https://github.com/microsoft/vswhere) : fichier exécutable C++ qui vous permet de rechercher l’emplacement des principaux outils Visual Studio à partir d’une instance installée de Visual Studio.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell) : scripts PowerShell qui utilisent l’API de configuration de l’installation pour identifier les instances installées de Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples) : exemples C# et C++ qui montrent comment utiliser l’API de configuration de l’installation pour interroger une installation existante.

De plus, l’[API de configuration de l’installation](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) fournit des interfaces destinées aux développeurs qui veulent créer leurs propres utilitaires d’interrogation des instances de Visual Studio.

>[!TIP]
>Pour plus d’informations sur l’installation de Visual Studio 2017, consultez les [articles de blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio 2017](install-visual-studio.md)
* [Créer un programme d’installation hors connexion pour Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Signaler un problème avec Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

