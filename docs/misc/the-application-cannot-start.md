---
title: "The application cannot start. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0001"
  - "vs.message.VB_E_IDACANTBOOT"
ms.assetid: ffc123a0-99e1-4e9d-8f6e-34aa357bf98f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The application cannot start.
Une erreur inattendue a empêché le démarrage de Visual Studio.  Cette erreur s'affiche quand l'une des conditions suivantes se vérifie :  
  
-   L'environnement de développement intégré \(IDE\) n'a pas pu charger Msxml3.dll.  
  
-   L'IDE n'a pas pu charger Mso.dll.  
  
-   L'IDE n'a pas pu charger DTE.olb.  
  
-   La clé de licence pour Visual Studio n'a pas été créée pendant l'installation.  
  
-   Le blocage de script est activé et n'autorise pas l'exécution du code des scripts.  
  
-   L'installation du .NET Framework, composant requis par Visual Studio, n'a pas réussi à générer une image native valide pour mscorlib.dll.  
  
-   Le virus Klez est présent sur votre ordinateur.  
  
 Pour corriger l'erreur, utilisez les procédures suivantes.  
  
> [!WARNING]
>  Certaines de ces résolutions nécessitent une modification de la clé de Registre.  L'utilisation incorrecte de l'Éditeur du Registre peut provoquer de sérieux problèmes qui peuvent nécessiter la réinstallation du système d'exploitation.  Microsoft ne peut pas garantir que vous puissiez résoudre les problèmes qui résultent d'une utilisation incorrecte de l'Éditeur du Registre.  Utilisez\-le à vos risques et périls.  
  
 L'IDE n'a pas pu charger Msxml3.dll.  
 La version bêta de juillet 2001 de MSXML 4.0 Technology Preview a laissé l'ordinateur dans un état à l'origine de ce comportement.  Pour réparer l'inscription de Msxml3.dll, procédez comme suit :  
  
### Désinstallez Msxml4.dll  
  
1.  Dans le menu **Démarrer**, cliquez sur **Exécuter**.  
  
2.  Dans la zone de texte **Ouvrir**, tapez `regsvr32 /u c:\winnt\system32\msxml4.dll` et cliquez sur **OK**.  
  
### Téléchargez et installez la mise à jour de sécurité pour MSXML  
  
1.  Téléchargez la mise à jour de sécurité la plus récente pour la version de MSXML que vous avez sur votre ordinateur à partir de [http:\/\/www.microsoft.com\/windows\/ie\/downloads\/critical\/q317244\/download.asp](http://www.microsoft.com/windows/ie/downloads/critical/q317244/download.asp).  
  
2.  Exécutez le fichier .exe pour la mise à jour de sécurité.  
  
### Téléchargez et appliquez les valeurs du Registre mises à jour  
  
1.  Téléchargez les valeurs du Registre mises à jour à partir de [http:\/\/download.microsoft.com\/download\/VisualStudioNET\/fix\/1.0\/WIN98MeXP\/Fixxml4.exe](http://download.microsoft.com/download/VisualStudioNET/fix/1.0/WIN98MeXP/Fixxml4.exe).  
  
2.  Double\-cliquez sur fixxml4.exe et décompressez les fichiers.  
  
3.  Recherchez Fixxml4.reg et double\-cliquez sur le fichier pour mettre à jour les valeurs du Registre.  
  
 L'IDE n'a pas pu charger Mso.dll.  
 Utilisez la liste suivante pour résoudre les problèmes posés par Mso.dll.  
  
### Microsoft Office  
  
-   Désinstallez toutes les versions bêta Microsoft Office XP installées sur votre ordinateur.  
  
-   Réparez Office XP via Ajout\/Suppression de programmes.  
  
-   Dans l'Éditeur du Registre, vérifiez la clé de Registre suivante :  
  
     `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0\Path] "MSO"="C:\Program Files\Common Files\Microsoft Shared\Office10\MSO.DLL"`  
  
 L'IDE n'a pas pu charger DTE.olb.  
 Pour corriger cette erreur :  
  
### Inscrivez Dte.olb  
  
1.  Dans le menu **Démarrer**, cliquez sur **Exécuter**.  
  
2.  Dans la zone de texte **Ouvrir**, tapez `regsvr32 C:\Program Files\Common Files\Microsoft Shared\MSEnv\DTE.OLB` et cliquez sur **OK**.  
  
 La clé de licence pour Visual Studio n'a pas été créée pendant l'installation.  
 Si l'écran de démarrage de Visual Studio ne contient pas une liste des produits installés et n'inclut pas d'informations sur la personne qui a installé le produit, la clé de licence est manquante.  De même, si Visual Studio n'est pas répertorié dans la boîte de dialogue Ajout\/Suppression de programmes, la clé de licence est manquante.  
  
 Pour résoudre ce problème :  
  
### Créez une clé de licence pour Visual Studio  
  
-   Supprimez complètement Visual Studio de l'ordinateur, puis réinstallez le produit.  
  
 Le blocage de script est activé et n'autorise pas l'exécution du code des scripts.  
 Si le blocage de script est activé pour une application tierce, l'IDE apparaît, puis disparaît.  
  
-   Pour corriger ce problème, vérifiez que la fonctionnalité de blocage de script fonctionne correctement.  
  
 L'installation du .NET Framework, composant requis par Visual Studio, n'a pas réussi à générer une image native valide pour mscorlib.dll.  
 Si l'écran de démarrage de Visual Studio apparaît brièvement, puis disparaît, il vous manque peut\-être une image native valide pour le fichier Mscorlib.dll.  Ce fichier est créé pendant l'installation du .NET Framework dans le répertoire \\%windir%\\assembly\\NativeImages1\_v1.0.3705\\mscorlib.  
  
 Pour corriger ce problème :  
  
### Créez un fichier Mscorlib.dll valide  
  
1.  Désinstallez, puis réinstallez le .NET Framework.  
  
 Le virus Klez est présent sur votre ordinateur.  
 Si votre ordinateur est infecté par le virus Klez, l'erreur suivante peut apparaître : « Impossible de démarrer l'application. ».  Il vous est recommandé de mettre à jour votre antivirus, puis d'analyser votre ordinateur.