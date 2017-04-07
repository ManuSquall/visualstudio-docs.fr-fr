---
title: "Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
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
ms.sourcegitcommit: 1d1e0c656b91049ce53456e6c5c011c08ca2e58e
ms.openlocfilehash: db051eaf8ef98928c0fec858e4cc9380a3b7687b
ms.lasthandoff: 03/11/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Appliquer automatiquement des clés de produit lors du déploiement de Visual Studio
Vous pouvez appliquer votre clé de produit par programmation dans le cadre du script utilisé pour automatiser le déploiement de Visual Studio. Les clés de produit peuvent être définies sur un appareil par programmation pendant l'installation de Visual Studio ou au terme d'une installation.  
  
## <a name="apply-the-license-during-installation"></a>Appliquer la licence pendant l'installation  
 Utilisez le paramètre --productKey pour appliquer une clé de produit au cours du processus d’installation de Visual Studio. Ce paramètre de configuration peut être utilisé avec le paramètre --quiet pour installer Visual Studio dans un état déjà sous licence pour un utilisateur final. Pour utiliser le paramètre --productKey, ouvrez une invite de commande. Exécutez le programme d’installation (par exemple, vs_enterprise.exe ou vs_professional.exe), puis définissez le paramètre --productKey avec une clé de produit (25 caractères) avec ou sans tirets :  
  
 Voici un exemple de commande destinée à installer Visual Studio 2015 Enterprise avec la clé de produit AAAAABBBBBCCCCCDDDDDEEEEEEE :  
  
 `vs_enterprise.exe [any other setup parameters] --productKey AAAAABBBBBCCCCCDDDDDDEEEEEE`  
  
## <a name="apply-the-license-after-installation"></a>Appliquer la licence après l’installation  
 Vous pouvez activer une version installée de Visual Studio avec une clé de produit à l'aide de l'utilitaire storePID.exe sur les ordinateurs cibles en mode silencieux. StorePID.exe est un programme utilitaire qui s’installe avec Visual Studio à l’adresse **\<drive>:\\\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe**.  
  
 Exécutez storePID.exe avec des privilèges élevés à l'aide d'un agent System Center ou d'une invite de commandes avec élévation de privilèges. Tapez ensuite la clé de produit (en incluant les tirets) et le code de produit Microsoft (MPC). Veillez à inclure les tirets de la clé de produit !  
  
 `StorePID.exe [product key including the dashes] [MPC]`  
  
 Voici un exemple de ligne de commande visant à installer Visual Studio 2017 Enterprise, qui a un MPC de 08860, avec une clé de produit « AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE » :  
  
 `C:\Program Files (x86)\Microsoft Visual Studio 15.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860`  
  
 Le tableau suivant répertorie les codes MPC pour chaque édition de Visual Studio :  
  
|Édition de Visual Studio|MPC|  
|---------------------------|---------|
|Visual Studio Enterprise 2017|08860|  
|Visual Studio Professional 2017|08862|  
|Visual Studio Test Professional 2017|08866| 
|Visual Studio Enterprise 2015|07060|  
|Visual Studio Professional 2015|07062|  
|Visual Studio Test Professional 2015|07066|  
|Visual Studio Ultimate 2013|06181|  
|Visual Studio Premium 2013|06191|  
|Visual Studio Professional 2013|06177|  
|Visual Studio Test Professional 2013|06194|  
  
Si la clé de produit est correctement appliquée, StorePID.exe retourne 0. Si elle rencontre des erreurs, elle renvoie un nombre compris entre 1 et 6.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Visual Studio](../install/install-visual-studio.md)
 [Créer une installation hors connexion de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
