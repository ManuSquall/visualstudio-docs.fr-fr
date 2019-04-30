---
title: 'Procédure : Signer des manifestes d’Application et déploiement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
caps.latest.revision: 61
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ddeb3fa5414208c610a7a21e176d55b0b0f985b5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435180"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Procédure : Application de connexion et les manifestes de déploiement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous souhaitez publier une application à l’aide du déploiement ClickOnce, vous devez signer les manifestes d’application et de déploiement avec une paire de clés publique/privée et à l’aide de la technologie Authenticode. Vous pouvez signer les manifestes à l’aide d’un certificat à partir du magasin de certificats Windows ou d’un fichier de clé.  
  
 Pour plus d’informations sur le déploiement ClickOnce, consultez [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
 La signature des manifestes ClickOnce est facultative pour les applications .exe. Pour plus d’informations, consultez la section « Génération de manifestes non signés » de ce document.  
  
 Pour plus d’informations sur la création des fichiers de clés, consultez [Guide pratique pour créer une paire de clés publique/privée](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).  
  
> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prend uniquement en charge les fichiers de clés PFX (Personal Information Exchange) portant l’extension .pfx. Toutefois, vous pouvez sélectionner d’autres types de certificats à partir du magasin de certificats Windows de l’utilisateur actuel en cliquant sur **Sélectionner dans Store** dans la page **Signature** des propriétés du projet.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>Pour signer des manifestes d’application et de déploiement à l’aide d’un certificat  
  
1. Accédez à la fenêtre des propriétés du projet (cliquez avec le bouton droit sur le nœud de projet dans l’**Explorateur de solutions** et sélectionnez **Propriétés** ou tapez **propriétés de projet** dans la fenêtre **Lancement rapide**, ou appuyez sur Alt+Entrée dans la fenêtre de l’**Explorateur de solutions**). Sous l’onglet **Signature**, cochez la case **Signer les manifestes ClickOnce**.  
  
2. Cliquez sur le bouton **Sélectionner dans Store**.  
  
     La boîte de dialogue **Sélectionner un certificat** apparaît et affiche le contenu du magasin de certificats Windows.  
  
    > [!TIP]
    > Si vous cliquez sur **Cliquez ici pour afficher les propriétés du certificat**, la boîte de dialogue **Détails du certificat** s’affiche. Cette boîte de dialogue inclut des informations détaillées sur le certificat et des options supplémentaires. Vous pouvez cliquer sur **Certificats** pour afficher des informations d’aide supplémentaires.  
  
3. Sélectionnez le certificat que vous souhaitez utiliser pour signer les manifestes.  
  
4. Vous pouvez aussi spécifier l’adresse d’un serveur d’horodatage dans la zone de texte **URL du serveur d’horodatage**. Ce serveur fournit un horodatage spécifiant quand le manifeste a été signé.  
  
### <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>Pour signer des manifestes d’application et de déploiement à l’aide d’un fichier de clé existant  
  
1. Dans la page **Signature**, cochez la case **Signer les manifestes ClickOnce**.  
  
2. Cliquez sur le bouton **À partir d’un fichier**.  
  
     La boîte de dialogue **Sélectionner le fichier** s’affiche.  
  
3. Dans la boîte de dialogue **Sélectionner le fichier**, recherchez l’emplacement du fichier de clé (.pfx) que vous souhaitez utiliser, puis cliquez sur **Ouvrir**.  
  
    > [!NOTE]
    > Cette option prend uniquement en charge les fichiers ayant l’extension .pfx. Si vous avez un fichier de clé ou un certificat dans un autre format, stockez-le dans le magasin de certificats Windows et sélectionnez le certificat, comme indiqué dans la procédure précédente. L’objet du certificat sélectionné doit inclure la signature de code.  
  
     La boîte de dialogue **Entrez le mot de passe pour ouvrir le fichier** s’affiche. (Si le fichier .pfx est déjà stocké dans votre magasin de certificats Windows ou qu’il n’est pas protégé par un mot de passe, vous n’êtes pas invité à entrer un mot de passe.)  
  
4. Entrez le mot de passe pour accéder au fichier de clé et appuyez sur Entrée.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>Pour signer des manifestes d’application et de déploiement à l’aide d’un certificat de test  
  
1. Dans la page **Signature**, cochez la case **Signer les manifestes ClickOnce**.  
  
2. Pour créer un certificat de test, cliquez sur le bouton **Créer un certificat de test**.  
  
3. Dans la boîte de dialogue **Créer un certificat de test**, entrez un mot de passe pour sécuriser votre certificat de test.  
  
## <a name="generating-unsigned-manifests"></a>Génération de manifestes non signés  
 La signature des manifestes ClickOnce est facultative pour les applications .exe. Les procédures suivantes montrent comment générer des manifestes ClickOnce non signés.  
  
> [!IMPORTANT]
> Les manifestes non signés peuvent simplifier le développement et le test de votre application. Toutefois, ils présentent des problèmes de sécurité importants dans un environnement de production. N’envisagez l’utilisation de manifestes non signés que si votre application ClickOnce s’exécute sur des ordinateurs au sein d’un intranet complètement isolé d’Internet ou d’autres sources de code malveillant.  
  
 Par défaut, ClickOnce génère automatiquement des manifestes signés, sauf si un ou plusieurs fichiers sont spécifiquement exclus du hachage généré. En d’autres termes, la publication de l’application aboutit à des manifestes signés si tous les fichiers sont inclus dans le hachage, même si la case **Signer les manifestes ClickOnce** n’est pas cochée.  
  
#### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Pour générer des manifestes non signés et inclure tous les fichiers dans le hachage généré  
  
1. Pour générer des manifestes non signés qui incluent tous les fichiers dans le hachage, vous devez d’abord publier l’application avec des manifestes signés. Vous devez donc signer les manifestes ClickOnce en effectuant l’une des procédures précédentes, puis publier l’application.  
  
2. Dans la page **Signature**, décochez la case **Signer les manifestes ClickOnce**.  
  
3. Redéfinissez la version de publication afin qu’une seule version de votre application soit disponible. Par défaut, Visual Studio incrémente automatiquement le numéro de révision de la version de publication chaque fois que vous publiez une application. Pour plus d'informations, voir [Procédure : Définir la publication ClickOnce Version](../deployment/how-to-set-the-clickonce-publish-version.md).  
  
4. Publiez l'application.  
  
#### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Pour générer des manifestes non signés et exclure un ou plusieurs fichiers du hachage généré  
  
1. Dans la page **Signature**, décochez la case **Signer les manifestes ClickOnce**.  
  
2. Ouvrez la boîte de dialogue **Fichiers d’application** et définissez le **Hachage** sur **Exclure** pour les fichiers que vous souhaitez exclure du hachage généré.  
  
    > [!NOTE]
    > Quand un fichier est exclu du hachage, ClickOnce est configuré pour désactiver la signature automatique des manifestes ; vous n’avez donc pas besoin de procéder à une publication préalable avec des manifestes signés comme indiqué dans la procédure précédente.  
  
3. Publiez l'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys avec nom fort](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Guide pratique pour Créer une paire de clés publique / privée](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)   
 [Page Signature, Concepteur de projet](../ide/reference/signing-page-project-designer.md)   
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)
