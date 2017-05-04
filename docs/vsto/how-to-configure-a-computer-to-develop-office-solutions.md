---
title: "Comment configurer un ordinateur pour d&#233;velopper des solutions Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "développement Office dans Visual Studio, installer des outils"
  - "composants requis (développement Office dans Visual Studio)"
ms.assetid: 76b463dc-43f0-47a1-845b-fe0a5e14bd80
caps.latest.revision: 130
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 129
---
# Comment configurer un ordinateur pour d&#233;velopper des solutions Office
  Pour configurer un ordinateur de développement de manière à pouvoir utiliser les Outils de développement Microsoft Office dans Visual Studio, suivez les instructions de cette rubrique.  Vous devez détenir des privilèges d'administrateur sur l'ordinateur de développement pour effectuer ces étapes.  
  
### Pour configurer l'ordinateur de développement  
  
1.  Installez une version de Visual Studio qui inclut les Outils de développement Office.  Les Outils de développement Microsoft Office sont installés par défaut.  Si vous personnalisez l'installation de Visual Studio en sélectionnant les composants à installer, assurez\-vous de sélectionner **Outils de développement Microsoft Office** lors de l'installation. Pour plus d'informations sur les versions de Visual Studio qui incluent les Outils de développement Office, consultez [Configuration d'un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
2.  Installez une version d'Office prise en charge par les Outils de développement Office dans Visual Studio.  Pour plus d'informations, consultez [Configuration d'un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
     Assurez\-vous également d'installer les assemblys PIA pour la version d'Office que vous installez.  Les assemblys PIA sont installés avec Office par défaut.  Si vous modifiez le programme d'installation d'Office, vérifiez que la fonctionnalité **Prise en charge de la programmabilité .NET** est sélectionnée pour les applications à cibler.  
  
3.  Si vous disposez d'une version anglaise de Visual Studio, mais que vous utilisez des paramètres autres que l'anglais pour Windows, vous pouvez installer le module linguistique [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pour afficher les messages de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dans la même langue que celle de Windows.  Les versions non anglaises de Visual Studio installent automatiquement le module linguistique.  Le module linguistique est disponible à partir du [Centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## Voir aussi  
 [Nouveautés du développement Office](http://msdn.microsoft.com/fr-fr/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Mise en route &#40;Développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Comment : installer Visual Studio Tools pour Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Comment : installer les assemblys PIA &#40;Primary Interop Assembly&#41; d'Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  