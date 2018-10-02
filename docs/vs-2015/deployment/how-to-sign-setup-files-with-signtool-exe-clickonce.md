---
title: 'Comment : signer des fichiers avec SignTool.exe (ClickOnce) d’installation | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, signtool.exe
- deploying applications [ClickOnce], re-signing setup.exe
- ClickOnce deployment, signtool.exe
- ClickOnce applications, re-signing setup.exe
- ClickOnce deployment, re-signing setup.exe
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ad234b1c21030032428265e9c03528a165cba8c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507325"
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Comment : signer des fichiers d'installation avec SignTool.exe (ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : signer les fichiers d’installation avec SignTool.exe (ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/how-to-sign-setup-files-with-signtool-exe-clickonce).  
  
Vous pouvez utiliser SignTool.exe pour signer un programme d'installation (setup.exe). Ce processus aide à garantir que les fichiers falsifiés ne sont pas installés sur les ordinateurs des utilisateurs finaux.  
  
 Par défaut, ClickOnce dispose de manifestes signés, ainsi que d'un programme d'installation signé. Toutefois, si vous souhaitez modifier ultérieurement les paramètres du programme d'installation, vous devrez également signer le programme d'installation. Si vous modifiez les paramètres après avoir signé le programme d'installation, la signature sera endommagée.  
  
 La procédure suivante génère des manifestes non signés ainsi qu'un programme d'installation non signé. La signature ClickOnce est ensuite activée dans Visual Studio pour générer des manifestes signés. Le programme d'installation n'est pas signé pour que les clients puissent signer l'exécutable avec leurs propres certificats.  
  
### <a name="to-generate-an-unsigned-setup-program-and-sign-later"></a>Pour générer un programme d'installation non signé et le signer ultérieurement  
  
1.  Sur l'ordinateur de développement, installez le certificat avec lequel vous souhaitez signer les manifestes.  
  
2.  Sélectionnez le projet dans **l’Explorateur de solutions**.  
  
3.  Sur le **projet** menu, cliquez sur *nom_projet* **propriétés**.  
  
4.  Dans le **signature** page, désactivez **signer les manifestes ClickOnce**.  
  
5.  Dans le **publier** , cliquez sur **conditions préalables**.  
  
6.  Vérifiez que toutes les conditions préalables sont sélectionnées, puis cliquez sur **OK**.  
  
7.  Dans le **publier** page, vérifiez les paramètres de publication, puis sur **publier maintenant**.  
  
     La solution publie le manifeste d’application non signé, le manifeste de déploiement non signé, les fichiers spécifiques à la version et le programme d’installation non signé à l’emplacement du dossier de publication.  
  
8.  Dans le **publier** , cliquez sur **conditions préalables**.  
  
9. Dans le **prérequis** boîte de dialogue, décochez **créer un programme d’installation pour installer les composants prérequis**.  
  
10. Dans le **publier** page, vérifiez les paramètres de publication, puis sur **publier maintenant**.  
  
     La solution publie le manifeste d’application signé, le manifeste de déploiement signé et les fichiers spécifiques à la version à l’emplacement du dossier de publication. Le programme d'installation non signé n'est pas remplacé par le processus de publication.  
  
11. Sur le site du client, ouvrez une invite de commandes.  
  
12. Accédez au répertoire qui contient le fichier .exe.  
  
13. Signez le fichier .exe à l'aide de la commande suivante :  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     Par exemple, pour signer le programme d'installation, utilisez l'une des commandes suivantes :  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour resigner des manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md)


