---
title: "Proc&#233;dure&#160;: annulation de l’inscription de VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exemples d’applications [SDK de Visual Studio], désinstallation"
  - "installation, VSPackages"
ms.assetid: b51522f0-c033-4d93-b928-2171a953032b
caps.latest.revision: 14
caps.handback.revision: 14
manager: "douge"
---
# Proc&#233;dure&#160;: annulation de l’inscription de VSPackages
Par défaut, lorsque vous générez des VSPackages, ils sont inscrits dans la ruche de Registre expérimentale. Votre ruche expérimentale peut se remplir de VSPackages que vous ne souhaitez pas conserver une fois que vous en avez fini avec eux.  
  
 Pour supprimer tous les packages qui sont inscrits dans la ruche expérimentale, il suffit de réinitialiser la ruche en exécutant l’outil CreateExpInstance avec l’option \/Reset. Pour plus d'informations, consultez [L'Instance expérimentale](../extensibility/the-experimental-instance.md).  
  
## Annulation de l’inscription de VSPackages spécifiques  
  
#### Pour annuler l’inscription d’un VSPackage non managé  
  
1.  Cliquez sur **Démarrer**, sur **Exécuter**, tapez `regsvr32 /u` *chemin\_VSPackage.dll*, puis cliquez sur OK.  
  
 Étant donné que les VSPackages non managés contiennent du code d’auto\-inscription, vous pouvez utiliser l’utilitaire regsvr32 pour les inscrire et les désinscrire.  
  
#### Pour annuler l’inscription d’un VSPackage managé  
  
1.  Cliquez sur **Démarrer**, sur **Exécuter** tapez *chemin\_installation\_kit\_SDK\_Visual Studio*`\EnvSDK\tools\bin\x86\regpkg /unregister` *chemin\_VSPackage.dll*, puis cliquez sur OK.  
  
 L’outil RegPkg lit les attributs d’inscription qui peuvent être incorporés dans un VSPackage managé. Le commutateur **\/unregister** fait en sorte que RegPkg supprime les informations du Registre.  
  
## Voir aussi  
 [Visual Studio Integration Samples](http://msdn.microsoft.com/fr-fr/b5dbf078-3af2-4fed-a1ea-171e4ee73a43)