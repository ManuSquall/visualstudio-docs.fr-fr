---
title: "Guide de l’administrateur Visual Studio │ Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
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
ms.translationtype: Human Translation
ms.sourcegitcommit: b5b496e0de0a12c9f52c944ef9e768c82d9be783
ms.openlocfilehash: c88a932beac964117ac2fd6ffe171bf4256ac706
ms.contentlocale: fr-fr
ms.lasthandoff: 05/08/2017

---
# <a name="visual-studio-2017-administrator-guide"></a>Guide de l’administrateur Visual Studio 2017

Dans les environnements d’entreprise, il est courant pour les administrateurs système de déployer des installations sur les utilisateurs finaux à partir d’un partage réseau ou à l’aide d’un logiciel de gestion de systèmes. Nous avons conçu le moteur d’installation de Visual Studio pour prendre en charge le déploiement d’entreprise, ce qui permet aux administrateurs système de créer un emplacement d’installation réseau pour préconfigurer les paramètres d’installation par défaut, déployer des clés de produit pendant le processus d’installation et gérer les mises à jour de produit après un déploiement réussi. Ce guide de l’administrateur fournit des conseils basés sur des scénarios pour un déploiement d’entreprise dans les environnements réseau courants.

## <a name="steps-for-deploying-visual-studio-2017-in-an-enterprise-environment"></a>Étapes du déploiement de Visual Studio 2017 dans un environnement d’entreprise

Vous pouvez déployer Visual Studio 2017 sur les stations de travail clientes tant que chaque ordinateur cible satisfait aux [conditions d’installation minimales](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Que votre déploiement s’effectue à l’aide de logiciels comme System Center ou à l’aide d’un fichier de commandes, vous voulez généralement effectuer les étapes suivantes :

1. [Créer un partage réseau contenant les fichiers du produit Visual Studio](create-a-network-installation-of-visual-studio.md) à un emplacement réseau.

2. [Sélectionner les charges de travail et les composants](workload-and-component-ids.md) à installer.

3. [Créer un fichier réponse](automated-installation-with-response-file.md) contenant les options d’installation par défaut. Vous pouvez aussi [générer un script d’installation](use-command-line-parameters-to-install-visual-studio.md) à l’aide des paramètres de ligne de commande pour contrôler l’installation.

4. Si vous le souhaitez, vous pouvez [appliquer une clé de produit de licence en volume](automatically-apply-product-keys-when-deploying-visual-studio.md) dans le cadre du script d’installation afin que les utilisateurs n’aient pas à activer le logiciel séparément.

5. Mettre à jour la disposition réseau pour [contrôler le moment où les mises à jour de produit sont remises aux utilisateurs finaux](controlling-updates-to-visual-studio-deployments.md).

6. Si vous le souhaitez, vous pouvez définir des clés de Registre pour [contrôler les éléments mis en cache sur les stations de travail clientes](set-defaults-for-enterprise-deployments.md).

7. Utiliser la technologie de déploiement de votre choix pour exécuter le script généré dans les étapes précédentes sur vos stations de travail de développement cibles.

8. [Actualiser votre emplacement réseau avec les dernières mises à jour](update-a-network-installation-of-visual-studio.md) de Visual Studio en exécutant régulièrement la commande utilisée à l’étape 1 pour ajouter des composants mis à jour.

> [!IMPORTANT]
> Notez que les installations effectuées à partir d’un partage réseau « se souviennent » de l’emplacement source dont elles sont issues. Cela signifie que la réparation d’un ordinateur client peut devoir retourner sur le partage réseau à partir duquel le client a été initialement installé. Choisissez soigneusement votre emplacement réseau : sa durée de vie doit être au moins aussi longue que celle des clients Visual Studio 2017 qui s’exécutent dans votre organisation.

## <a name="tools"></a>Outils
Nous avons mis à disposition plusieurs outils qui vous aideront à [détecter et gérer les instances de Visual Studio installées](tools-for-managing-visual-studio-instances.md) sur les ordinateurs clients.

> [!TIP]
> Outre la documentation du guide de l’administrateur, le [blog d’Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/) constitue une bonne source d’informations sur l’installation de Visual Studio 2017.

## <a name="see-also"></a>Voir aussi
* [Installer Visual Studio 2017](install-visual-studio.md)
* [Installer Visual Studio dans des environnements hors connexion](install-visual-studio-in-offline-environment.md)
* [Utiliser les paramètres de ligne de commande pour installer Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemples de paramètres de ligne de commande](command-line-parameter-examples.md)
* [Signaler un problème avec Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

