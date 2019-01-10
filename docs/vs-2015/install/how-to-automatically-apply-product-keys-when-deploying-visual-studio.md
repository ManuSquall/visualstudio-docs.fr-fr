---
title: 'Procédure : Appliquer automatiquement les clés de produit lors du déploiement de Visual Studio 2015 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 11
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 1dd9127895a375ae02e6d4f18bae0a09bef494bb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942042"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>Procédure : Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour la documentation la plus récente pour Visual Studio 2017, consultez [appliquer automatiquement les clés de produit lors du déploiement de Visual Studio](/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio).

Vous pouvez appliquer votre clé de produit par programmation dans le cadre du script utilisé pour automatiser le déploiement de Visual Studio 2015. Les clés de produit peuvent être définies sur un appareil par programmation pendant l'installation de Visual Studio ou au terme d'une installation.

## <a name="apply-the-license-during-installation"></a>Appliquer la licence pendant l'installation
 Utilisez le paramètre /ProductKey pour appliquer une clé de produit au cours du processus d'installation de Visual Studio. Ce paramètre de configuration peut être utilisé avec le paramètre /Silent pour installer Visual Studio dans un état déjà sous licence pour un utilisateur final. Pour utiliser le paramètre /ProductKey, ouvrez une invite de commande. Exécutez le programme d’installation (par exemple, vs_enterprise.exe ou vs_professional.exe), puis définissez le paramètre /ProductKey avec une clé de produit (25 caractères), sans tirets :

 Voici un exemple de commande destinée à installer Visual Studio 2015 Enterprise avec la clé de produit AAAAABBBBBCCCCCDDDDDEEEEEEE :

 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`

## <a name="apply-the-license-after-installation"></a>Appliquer la licence après l’installation
 Vous pouvez activer une version installée de Visual Studio avec une clé de produit à l'aide de l'utilitaire storePID.exe sur les ordinateurs cibles en mode silencieux. StorePID.exe est un programme utilitaire qui s’installe avec Visual Studio à l’adresse **\<lecteur>:\\\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**.

 Exécutez storePID.exe avec des privilèges élevés à l'aide d'un agent System Center ou d'une invite de commandes avec élévation de privilèges. Tapez ensuite la clé de produit (en incluant les tirets) et le code de produit Microsoft (MPC). Veillez à inclure les tirets de la clé de produit !

 `StorePID.exe [product key including the dashes] [MPC]`

 Voici un exemple de ligne de commande visant à installer Visual Studio 2015 Enterprise, qui a un MPC de 07060, avec une clé de produit « AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE » :

 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`

 Le tableau suivant répertorie les codes MPC pour chaque édition de Visual Studio :

|Édition de Visual Studio|MPC|
|---------------------------|---------|
|Visual Studio Enterprise 2015|07060|
|Visual Studio Professional 2015|07062|
|Visual Studio Test Professional 2015|07066|
|Visual Studio Ultimate 2013|06181|
|Visual Studio Premium 2013|06191|
|Visual Studio Professional 2013|06177|
|Visual Studio Test Professional 2013|06194|

 Pour plus d’informations sur l’obtention d’une clé de produit, consultez [Comment : Recherchez la clé de produit Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md).

 Si la clé de produit est correctement appliquée, StorePID.exe retourne 0. Si elle rencontre des erreurs, elle renvoie un nombre compris entre 1 et 6.

## <a name="see-also"></a>Voir aussi
 [Installer Visual Studio](../install/install-visual-studio-2015.md)