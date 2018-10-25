---
title: 'Comment : publier une Application ClickOnce à l’aide de l’Assistant Publication | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07a4c1178859a3b5884e0573bde31ed251e8a68f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899004"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Comment : publier une application ClickOnce à l’aide de l’Assistant Publication
Pour mettre une application ClickOnce à la disposition des utilisateurs, vous devez la publier sur un partage de fichiers ou un chemin d’accès, un serveur FTP ou un média amovible. Vous pouvez publier l’application à l’aide de l’Assistant Publication ; propriétés supplémentaires liées à la publication sont disponibles sur le **publier** page de la **Concepteur de projet**. Pour plus d’informations, consultez [publication ClickOnce applications](../deployment/publishing-clickonce-applications.md).  
  
 Avant d'exécuter l'Assistant Publication, vous devez correctement définir les propriétés de publication. Par exemple, si vous souhaitez spécifier une clé pour signer votre application ClickOnce, vous pouvez le faire ainsi de suite le **signature** page de la **Concepteur de projet**. Pour plus d’informations, consultez [applications ClickOnce Secure](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Lorsque vous installez plusieurs versions d’une application à l’aide de ClickOnce, l’installation déplace les versions antérieures de l’application dans un dossier nommé *Archive*, dans l’emplacement de publication que vous spécifiez. Cet archivage permet d’éviter la présence de dossiers de la version précédente dans le répertoire d’installation.  
  
> [!NOTE]
>  Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier ces paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>Pour publier vers un partage de fichiers ou un chemin d’accès  
  
1. Dans **l’Explorateur de solutions**, sélectionnez le projet d’application.  
  
2. Sur le **Build** menu, cliquez sur **publier** *nom_projet*.  
  
    L'Assistant Publication apparaît.  
  
3. Dans le **où voulez-vous publier l’application ?** page, entrez une adresse de serveur FTP valide ou un chemin d’accès de fichier valide à l’aide d’un des formats indiqués, puis cliquez sur **suivant**.  
  
4. Dans le **comment les utilisateurs installeront-ils l’application ?** page, sélectionnez l’emplacement où les utilisateurs devront accéder pour installer l’application :  
  
   -   Si les utilisateurs installent à partir d’un site Web, cliquez sur **à partir d’un site Web** et entrez une URL qui correspond au chemin de fichier entré à l’étape précédente. Cliquez sur **Suivant**. (Cette option est généralement utilisée quand vous spécifiez une adresse FTP comme emplacement de publication. Le téléchargement direct à partir de FTP n'est pas pris en charge. Vous devez donc entrer une URL ici.)   
  
   -   Si les utilisateurs installent l’application directement à partir du partage de fichiers, cliquez sur **à partir d’un fichier ou chemin d’accès lecteur UNC**, puis cliquez sur **suivant**. (Il s’agit de la publication des emplacements du formulaire *c:\deploy\myapp* ou  *\\\server\myapp*.)  
  
   -   Si les utilisateurs installent à partir d’un support amovible, cliquez sur **à partir d’un CD-ROM ou DVD-ROM**, puis cliquez sur **suivant**.  
  
5. Sur le **l’application sera-t-elle disponible hors connexion ?** , cliquez sur l’option appropriée :  
  
   - Si vous souhaitez activer l’application à exécuter lorsque l’utilisateur est déconnecté du réseau, cliquez sur **Oui, cette application sera disponible en ligne ou hors connexion**. Un raccourci sur le **Démarrer** menu sera créé pour l’application.  
  
   - Si vous souhaitez exécuter l’application directement à partir de l’emplacement de publication, cliquez sur **non, cette application est uniquement disponible en ligne**. Un raccourci sur le **Démarrer** menu ne sera pas créé.  
  
     Cliquez sur **Suivant** pour continuer.  
  
6. Cliquez sur **Terminer** pour publier l’application.  
  
    L'état de publication s'affiche dans la zone de notification d'état.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Pour publier sur un CD-ROM ou DVD-ROM  
  
1. Dans **l’Explorateur de solutions**, cliquez sur le projet d’application et cliquez sur **propriétés**.  
  
    Le **Concepteur de projet** s’affiche.  
  
2. Cliquez sur le **publier** onglet pour ouvrir le **publier** page dans le **Concepteur de projets**et cliquez sur le **Assistant Publication** bouton.  
  
    L'Assistant Publication apparaît.  
  
3. Dans le **où voulez-vous publier l’application ?** , entrez le chemin d’accès de fichier ou l’emplacement FTP où l’application sera publiée, par exemple *d:\deploy*. Puis cliquez sur **suivant** pour continuer.  
  
4. Sur le **comment les utilisateurs installeront-ils l’application ?** , cliquez sur à partir d’un **CD-ROM ou DVD-ROM**, puis cliquez sur **suivant**.  
  
   > [!NOTE]
   >  Si vous souhaitez que l’installation s’exécute automatiquement lorsque le CD-ROM est inséré dans le lecteur, ouvrez le **publier** page dans le **Concepteur de projets** et cliquez sur le **Options** bouton, puis, dans le **Options de publication** Assistant, sélectionnez **installations pour CD-ROM, démarrer automatiquement l’installation lorsque le CD est inséré**.  
  
5. Si vous distribuez votre application sur CD-ROM, vous souhaitez peut-être fournir des mises à jour à partir d’un site web. Dans le **où l’application doit-elle vérifier les mises à jour ?** page, choisissez une option de mise à jour :  
  
   - Si l’application doit vérifier les mises à jour, cliquez sur **l’application vérifie les mises à jour à partir de l’emplacement suivant** et entrez l’emplacement où les mises à jour seront publiées. Il peut s’agir d’un emplacement de fichier, d’un site web ou d’un serveur FTP.  
  
   - Si l’application ne doit pas vérifier les mises à jour, cliquez sur **l’application ne vérifie pas les mises à jour**.  
  
     Cliquez sur **Suivant** pour continuer.  
  
6. Cliquez sur **Terminer** pour publier l’application.  
  
    L'état de publication s'affiche dans la zone de notification d'état.  
  
   > [!NOTE]
   >  Une fois la publication terminée, vous devez utiliser un graveur de CD ou de DVD pour copier les fichiers depuis l'emplacement spécifié à l'étape 3 sur le CD-ROM ou DVD-ROM.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Sécuriser les applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Déploiement d’une solution Office à l’aide de ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)