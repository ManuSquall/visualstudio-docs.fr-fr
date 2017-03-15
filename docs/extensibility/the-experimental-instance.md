---
title: "L&#39;Instance exp&#233;rimentale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "builds expérimentales"
  - "VSPackages, builds expérimentales"
  - "VSIP, builds expérimentales"
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# L&#39;Instance exp&#233;rimentale
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour protéger votre environnement de développement Visual Studio à partir d'applications non testées qui peut modifier, VSSDK fournit un espace expérimental que vous pouvez utiliser pour faire des essais. Vous développez des applications à l'aide de Visual Studio comme d'habitude, mais les exécuter à l'aide de cette instance expérimentale.  
  
 Chaque application qui dispose d'un package VSIX lance l'instance expérimentale de Visual Studio en mode débogage.  
  
 Si vous souhaitez démarrer l'instance expérimentale de Visual Studio en dehors d'une solution spécifique, exécutez la commande suivante dans la fenêtre de commande :  
  
 «*\< chemin d'installation de visual studio \>*\\Common7\\IDE\\devenv.exe "RootSuffix Exp  
  
> [!NOTE]
>  L'instance expérimentale est écrite dans le Registre sous le `<version number>Exp` et `<version number>Exp_Config` nœuds. Par exemple est la zone de Registre expérimentale de Visual Studio 2015  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` et `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Nous vous recommandons d'exécuter votre extension dans l'instance expérimentale lorsque vous le développez. Lorsque vous déployez l'extension, elle s'exécute dans l'instance de développement. Pour plus d'informations sur l'inscription des applications, consultez la page [L'enregistrement de packages VS](../extensibility/internals/registering-vspackages.md).