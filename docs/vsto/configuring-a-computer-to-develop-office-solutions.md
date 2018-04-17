---
title: Configuration d’un ordinateur pour développer des Solutions Office | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 59c00639ce839962c06cacf3c036a5cd8f74b508
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Configuration d'un ordinateur pour développer des solutions Office

Pour créer des compléments VSTO et des personnalisations pour Microsoft Office, installez une version prise en charge de Visual Studio, le .NET Framework et Microsoft Office.

|Logiciels|Versions prises en charge|
|--------------|------------------------|
|Visual Studio 2017| N’importe quelle édition avec le **développement d’Office/SharePoint** la charge de travail.|
|.NET Framework|-Le .NET Framework 4 ou version ultérieur.|
|Microsoft Office|<ul><li>Toute édition de la suite Office, y compris Office Professionnel Plus pour Office 365.</li><li>N'importe laquelle des applications autonomes suivantes :<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 et Office 2010 uniquement)</li><li>Outlook</li><li>PowerPoint</li><li>Projet</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic pour Applications (VBA) doit être installé dans le cadre d'Office. **Important :** -clic les versions des applications Office 2010 ne sont pas pris en charge.|

Pour les instructions d’installation détaillées, consultez [Comment : configurer un ordinateur pour développer des Solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Si les modèles de projet n’apparaissent pas ou ne fonctionnent pas dans Visual Studio

Si vous installez une version prise en charge de Visual Studio, le .NET Framework et Microsoft Office, mais les modèles de projet Office n’apparaissent pas dans Visual Studio **nouveau projet** boîte de dialogue, ou si vous recevez une erreur lorsque vous essayez d’utiliser un, Vérifiez les points suivants :

- Assurez-vous que les outils de développement Microsoft Office sont installés sur votre ordinateur.

     Les outils de développement Office sont un composant facultatif de Visual Studio, mais ils sont généralement installés automatiquement avec Visual Studio. Si vous personnalisez l'installation de Visual Studio en spécifiant les fonctionnalités à installer, assurez-vous de choisir **Outils de développement Microsoft Office** pendant l'installation, afin d'installer ces outils.

     Pour vous assurer que ces outils sont installés, démarrez le programme d’installation de Visual Studio et choisissez la **modifier** bouton. Cochez la case **Outils de développement Microsoft Office** , puis choisissez le bouton **Mettre à jour** .

- Assurez-vous que vous n’exécutez pas une version d’Office qui a été remis par clic. Consultez [Comment : vérifier si Outlook est une application « Démarrer en un clic » sur un ordinateur](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).

- Assurez-vous que vous exécutez qu’une seule version de Microsoft Office.

Si les problèmes persistent, consultez [Additional Support for Errors in Office Solutions](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Voir aussi

[Mise en route &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Guide pratique pour configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Guide pratique pour installer Visual Studio Tools pour Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Guide pratique pour installer les assemblys PIA (Primary Interop Assembly) d’Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md)
