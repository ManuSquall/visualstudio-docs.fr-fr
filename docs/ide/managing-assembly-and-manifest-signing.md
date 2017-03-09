---
title: "Gestion d&#39;assembly et signature de manifeste | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "manifestes (Visual Studio)"
  - "signer des manifestes (Visual Studio)"
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gestion d&#39;assembly et signature de manifeste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La signature avec nom fort donne une identité unique du composant logiciel a globalement.  Les noms forts sont utilisés pour garantir que l'assembly ne peut pas être il était rendu factice par quelqu'un d'autre, et pour vous assurer que les dépendances d'et la carte instructions de configuration au composant et à la version appropriée du composant.  
  
 Un nom fort est constitué de l'identité de l'assembly \(nom de texte simple, numéro de version et informations de culture\), ainsi que d'un jeton de clé publique et d'une signature numérique.  
  
 Pour plus d'informations sur la signature d'assemblys dans les projets Visual Basic et C\#, consultez [Création et utilisation d'assemblys avec nom fort](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md).  
  
 Pour plus d'informations sur la signature d'assemblys dans des projets Visual C\+\+, consultez [Assemblys de nom fort \(signature d'assembly\)](/visual-cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).  
  
## Types et signature de composant  
 Vous pouvez signer des assemblys et les manifestes d'application .NET.  et notamment :  
  
-   exécutables \(.exe\)  
  
-   manifestes d'application \(.exe.manifest\)  
  
-   manifestes de déploiement \(.application\)  
  
-   assemblys composants partagés \(.dll\)  
  
 Vous devez signer les types suivants de composant :  
  
1.  assemblys, si vous souhaitez les déployer dans le Global Assembly Cache \(GAC\).  
  
2.  Les manifestes d'application et de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Visual Studio vérifie la signature par défaut pour ces applications.  
  
3.  Les assemblys PIA \(Primary Interop Assembly\), qui sont utilisés pour l'interopérabilité COM.  L'utilitaire TLBIMP applique l'attribution de noms forts lors de la création d'un assembly PIA \(Primary Interop Assembly\) à partir d'une bibliothèque de types COM.  
  
 En général vous ne devez pas archiver les fichiers exécutables.  Un composant fortement nommé ne peut pas référencer un composant non\-fort\- nommé déployé avec l'application.  Visual Studio ne signe pas de fichiers exécutables d'application, mais signe à la place le manifeste d'application, qui affiche le fichier exécutable portant.  Vous devez généralement éviter la signature des composants privés pour votre application, car la signature peut compliquer la gestion des dépendances.  
  
## Signez procédure un assembly dans Visual Studio  
 Vous archivez une application ou un composant à l'aide de l'onglet **Signature** de la fenêtre de propriétés du projet \(cliquez avec le bouton droit sur le nœud de projet dans l'**Explorateur de solutions** et sélectionnez **Propriétés**, ou tapez les propriétés de projet dans la fenêtre **Lancement rapide**, ou appuyez sur ALT\+ ENTRÉE dans la fenêtre **Explorateur de solutions** \).  Sélectionnez l'onglet **Signature**, puis activez la case à cocher **Signer l'assembly** .  
  
 Spécifiez un fichier de clé.  Si vous choisissez de créer un nouveau fichier de clé, notez que de nouveaux fichiers de clés sont systématiquement créés au format .pfx.  Vous avez besoin d'un nom et un mot de passe du fichier.  
  
> [!WARNING]
>  Vous devez toujours protéger votre fichier de clé avec un mot de passe pour empêcher les tiers de l'utiliser.  Vous pouvez également sécuriser vos clés à l'aide de fournisseurs ou des magasins de certificats.  
  
 Vous pouvez également spécifier une clé que vous avez déjà créée.  Pour plus d'informations sur la création de clés, consultez [Comment : créer une paire de clés publique\/privée](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md).  
  
 Si vous avez accès à une clé publique, vous pouvez utiliser la temporisation de signature pour différer assigner la clé.  Pour activer la temporisation de signature en activant la case à cocher **Différer la signature uniquement**.  Un projet à signature différée ne fonctionnera pas, et vous ne pouvez pas le déboguer.  Toutefois, vous pouvez ignorer la vérification pendant le développement en utilisant [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) avec l'option `-Vr`.  
  
 Pour plus d'informations sur la signature des manifestes, consultez [Comment : signer des manifestes d'application et de déploiement](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
## Voir aussi  
 [Assemblys avec nom fort](../Topic/Strong-Named%20Assemblies.md)   
 [Assemblys de nom fort \(signature d'assembly\)](/visual-cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)