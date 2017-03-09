---
title: "Comment&#160;: signer des manifestes d&#39;application et de d&#233;ploiement | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "manifestes d'application (Visual Studio)"
  - "assemblys (Visual Studio), signer"
  - "ClickOnce (déploiement Visual Studio), signer des assemblys"
  - "signature du code (Visual Studio), Authenticode"
  - "manifestes de déploiement (Visual Studio)"
  - "fichiers de clés (Visual Studio)"
  - "manifestes (Visual Studio)"
  - "signer des manifestes (Visual Studio)"
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
caps.latest.revision: 58
caps.handback.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comment&#160;: signer des manifestes d&#39;application et de d&#233;ploiement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous souhaitez publier une application à l'aide du déploiement ClickOnce, les manifestes d'application et de déploiement doivent être signés avec une paire de clés publique\/privée et à l'aide de la technologie Authenticode.  Vous pouvez signer les manifestes à l'aide d'un certificat du magasin de certificats Windows ou d'un fichier de clé.  
  
 Pour plus d'informations sur le déploiement ClickOnce, consultez [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
 La signature des manifestes ClickOnce est facultative pour les applications .exe.  Pour plus d'informations, consultez la section « Génération de manifestes non signés » de ce document.  
  
 Pour plus d'informations sur la création de fichiers de clés, consultez [Comment : créer une paire de clés publique\/privée](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md).  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prend en charge uniquement les fichiers de clé PFX \(Échange d'informations personnelles\) portant l'extension .pfx.  Toutefois, vous pouvez sélectionner d'autres types de certificats dans le magasin de certificats Windows de l'utilisateur actuel en cliquant sur **À partir du magasin** sur la page **Signature** des propriétés de projet.  
  
### Pour signer les manifestes d'application et de déploiement à l'aide d'un certificat  
  
1.  Accédez à la fenêtre de propriétés du projet \(cliquez avec le bouton droit sur le nœud de projet dans l'**Explorateur de solutions** et sélectionnez **Propriétés** ou saisissez les propriétés de projet dans la fenêtre **Lancement rapide**, ou appuyez sur ALT\+ ENTRÉE dans la fenêtre **Explorateur de solutions**\).  Sur l'onglet **Signature**, activez la case à cocher **Signer les manifestes ClickOnce**.  
  
2.  Cliquez sur le bouton **À partir du magasin**.  
  
     La boîte de dialogue **Sélectionner un certificat** apparaît et affiche le contenu du magasin de certificats Windows.  
  
    > [!TIP]
    >  Si vous cliquez sur **Cliquez ici pour afficher les propriétés du certificat**, la boîte de dialogue **Détails du certificat** apparaît.  Cette boîte de dialogue contient des informations détaillées sur le certificat et inclut des options supplémentaires.  Vous pouvez cliquer sur **certificats** pour afficher l'aide supplémentaire.  
  
3.  Sélectionnez le certificat que vous souhaitez utiliser pour signer les manifestes.  
  
4.  Vous pouvez également spécifier l'adresse d'un serveur d'horodatage dans la zone de texte **URL du serveur d'horodatage**.  Il s'agit d'un serveur qui fournit un horodatage spécifiant le moment où le manifeste a été signé.  
  
### Pour signer les manifestes d'application et de déploiement à l'aide d'un fichier de clé existant  
  
1.  Sur la page **Signature**, activez la case à cocher **Signer les manifestes ClickOnce**.  
  
2.  Cliquez sur le bouton **À partir d'un fichier**.  
  
     La boîte de dialogue **Sélectionner le fichier** apparaît.  
  
3.  Dans la boîte de dialogue **Sélectionner le fichier**, accédez à l'emplacement du fichier de clé \(.pfx\) que vous souhaitez utiliser, puis cliquez sur **Ouvrir**.  
  
    > [!NOTE]
    >  Cette option prend en charge uniquement les fichiers avec l'extension .pfx.  Si vous avez un fichier de clé ou un certificat dans un autre format, stockez\-le dans le magasin de certificats Windows et sélectionnez le certificat décrit dans la procédure précédente.  L'objet du certificat sélectionné doit inclure la signature de code.  
  
     La boîte de dialogue **Entrez le mot de passe pour ouvrir le fichier** apparaît. \(Si le fichier .pfx est déjà stocké dans votre magasin de certificats Windows ou s'il n'est pas protégé par un mot de passe, vous ne serez pas invité à saisir un mot de passe.\)  
  
4.  Entrez le mot de passe pour accéder au fichier de clé et appuyez sur ENTRÉE.  
  
### Pour signer les manifestes d'application et de déploiement à l'aide d'un certificat de test  
  
1.  Sur la page **Signature**, activez la case à cocher **Signer les manifestes ClickOnce**.  
  
2.  Pour créer un nouveau certificat à des fins de test, cliquez sur le bouton **Créer un certificat de test**.  
  
3.  Dans la boîte de dialogue **Créer un certificat de test**, entrez un mot de passe pour sécuriser votre certificat de test.  
  
## Génération de manifestes non signés  
 La signature des manifestes ClickOnce est facultative pour les applications .exe.  Les procédures suivantes indiquent comment générer des manifestes ClickOnce non signés.  
  
> [!IMPORTANT]
>  Les manifestes non signés peuvent simplifier le développement et le test de votre application.  Toutefois, les manifestes non signés présentent des problèmes de sécurité importants dans un environnement de production.  Envisagez uniquement d'utiliser des manifestes non signés si votre application ClickOnce s'exécute sur des ordinateurs dans un intranet complètement isolé d'Internet ou autres sources de code malveillant.  
  
 Par défaut, ClickOnce génère automatiquement des manifestes non signés, sauf si un ou plusieurs fichiers sont spécifiquement exclus du hachage généré.  En d'autres termes, la publication de l'application génère des manifestes signés si tous les fichiers sont inclus dans le hachage, même si la case à cocher **Signer les manifestes ClickOnce** est désactivée.  
  
#### Pour générer des manifestes non signés et inclure tous les fichiers dans le hachage généré  
  
1.  Pour générer des manifestes non signés qui incluent tous les fichiers dans le hachage, vous devez tout d'abord publier l'application avec des manifestes signés.  Par conséquent, vous devez tout d'abord signer les manifestes ClickOnce en vous conformant à l'une des procédures précédentes et publier ensuite l'application.  
  
2.  Sur la page **Signature**, désactivez la case à cocher **Signer les manifestes ClickOnce**.  
  
3.  Redéfinissez la version publiée de sorte qu'une seule version de votre application soit disponible.  Par défaut, Visual Studio incrémente automatiquement le numéro de révision de la version publiée chaque fois que vous publiez une application.  Pour plus d'informations, consultez [How to: Set the ClickOnce Publish Version](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md).  
  
4.  Publiez l'application.  
  
#### Pour générer des manifestes non signés et exclure un ou plusieurs fichiers du hachage généré  
  
1.  Sur la page **Signature**, désactivez la case à cocher **Signer les manifestes ClickOnce**.  
  
2.  Ouvrez la boîte de dialogue **Fichiers d'application** et affectez **Exclure** à **Hachage** pour les fichiers que vous voulez exclure du hachage généré.  
  
    > [!NOTE]
    >  Lorsque vous excluez un fichier du hachage, ClickOnce est configuré pour désactiver automatiquement la signature des manifestes. Il est donc inutile de publier tout d'abord l'application avec des manifestes signés comme indiqué dans la procédure précédente.  
  
3.  Publiez l'application.  
  
## Voir aussi  
 [Assemblys avec nom fort](../Topic/Strong-Named%20Assemblies.md)   
 [Comment : créer une paire de clés publique\/privée](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md)   
 [Page Signature, Concepteur de projets](../ide/reference/signing-page-project-designer.md)   
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)