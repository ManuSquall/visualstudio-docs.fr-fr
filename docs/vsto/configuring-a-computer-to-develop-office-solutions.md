---
title: "Configuration d’un ordinateur pour développer des Solutions Office | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office development in Visual Studio, installing tools
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: "97"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2d3e0b354375d6116a1bcc0cc2b0d69ecc2f16b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Configuration d'un ordinateur pour développer des solutions Office
  Pour créer des compléments VSTO et des personnalisations pour Microsoft Office, installez une version prise en charge de Visual Studio, le .NET Framework et Microsoft Office.  
  
|Logiciels|Versions prises en charge|  
|--------------|------------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)]**Important :** vous devez sélectionner la case à cocher Outils de développement Microsoft Office pendant l’installation.|  
|.NET Framework|-Le .NET Framework 4 ou version ultérieur.|  
|Microsoft Office|<ul><li>Toute édition de la suite Office, y compris Office Professionnel Plus pour Office 365.</li><li>N'importe laquelle des applications autonomes suivantes :<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 et Office 2010 uniquement)</li><li>Outlook</li><li>PowerPoint</li><li>Projet</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic pour Applications (VBA) doit être installé dans le cadre d'Office. **Important :** -clic les versions des applications Office 2010 ne sont pas pris en charge.|  
  
 Pour les instructions d’installation détaillées, consultez [Comment : configurer un ordinateur pour développer des Solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Si les modèles de projet n’apparaissent pas ou ne fonctionnent pas dans Visual Studio  
 Si vous installez une version prise en charge de Visual Studio, le .NET Framework et Microsoft Office, mais les modèles de projet Office n’apparaissent pas dans Visual Studio **nouveau projet** boîte de dialogue, ou si vous recevez une erreur lorsque vous essayez d’utiliser un, Vérifiez les points suivants :  
  
-   Assurez-vous que les outils de développement Microsoft Office sont installés sur votre ordinateur.  
  
     Les outils de développement Office sont un composant facultatif de Visual Studio, mais ils sont généralement installés automatiquement avec Visual Studio. Si vous personnalisez l'installation de Visual Studio en spécifiant les fonctionnalités à installer, assurez-vous de choisir **Outils de développement Microsoft Office** pendant l'installation, afin d'installer ces outils.  
  
     Pour vous assurer que ces outils sont installés, démarrez le programme d'installation de Visual Studio et choisissez le bouton **Modifier** . Cochez la case **Outils de développement Microsoft Office** , puis choisissez le bouton **Mettre à jour** .  
  
-   Assurez-vous que vous n'exécutez pas une version d'Office de type « Démarrer en un clic ». Consultez [Comment : vérifier si Outlook est une application « Démarrer en un clic » sur un ordinateur](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).  
  
-   Assurez-vous que vous exécutez qu’une seule version de Microsoft Office.  
  
 Si les problèmes persistent, consultez [Additional Support for Errors in Office Solutions](../vsto/additional-support-for-errors-in-office-solutions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en route &#40; développement Office dans Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Comment : configurer un ordinateur pour développer des Solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Comment : installer Visual Studio Tools pour Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Comment : installer les assemblys PIA Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md)  
  
  