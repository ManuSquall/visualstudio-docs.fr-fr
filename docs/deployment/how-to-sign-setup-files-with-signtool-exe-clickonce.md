---
title: 'Comment : se connecter fichiers d’installation avec SignTool.exe (ClickOnce) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 4be6438f16ddf86afdc8139491d081bcd2fce7a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-sign-setup-files-with-signtoolexe-clickonce"></a>Comment : signer des fichiers d'installation avec SignTool.exe (ClickOnce)
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
  
9. Dans le **conditions préalables** boîte de dialogue, désactivez **créer un programme d’installation pour installer les composants requis**.  
  
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