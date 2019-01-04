---
title: Configurer un ordinateur pour développer des solutions Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47435fb5767b19ca36fc94387bdbefe3578f6325
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955943"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurer un ordinateur pour développer des solutions Office

Pour créer des compléments VSTO et des personnalisations pour Microsoft Office, installez une version prise en charge de Visual Studio, le .NET Framework et Microsoft Office.

|Logiciels|Versions prises en charge|
|--------------|------------------------|
|Visual Studio 2017| N’importe quelle édition avec le **développement Office/SharePoint** charge de travail.|
|.NET Framework|-.NET Framework 4 ou version ultérieur.|
|Microsoft Office|<ul><li>Toute édition de la suite Office, y compris Office Professionnel Plus pour Office 365.</li><li>N'importe laquelle des applications autonomes suivantes :<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 et Office 2010 uniquement)</li><li>Outlook</li><li>PowerPoint</li><li>Projet</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic pour Applications (VBA) doit être installé dans le cadre d'Office. **Important :** Les versions « Démarrer en un clic » des applications d'Office 2010 ne sont pas prises en charge.|

Pour les instructions d’installation détaillées, consultez [Comment : Configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Si les modèles de projet n’apparaissent pas ou ne fonctionnent pas dans Visual Studio

Si vous installez une version prise en charge de Visual Studio, le .NET Framework et Microsoft Office, mais les modèles de projet Office n’apparaissent pas dans Visual Studio **nouveau projet** boîte de dialogue, ou si vous recevez une erreur lorsque vous essayez d’utiliser un, Vérifiez les points suivants :

- Assurez-vous que les outils de développement Microsoft Office sont installés sur votre ordinateur.

     Outils de développement Office sont un composant facultatif de Visual Studio, mais ils sont installés automatiquement avec Visual Studio. Si vous personnalisez l'installation de Visual Studio en spécifiant les fonctionnalités à installer, assurez-vous de choisir **Outils de développement Microsoft Office** pendant l'installation, afin d'installer ces outils.

     Pour vous assurer que ces outils sont installés, démarrez le programme d’installation de Visual Studio, puis choisissez le **modifier** bouton. Cochez la case **Outils de développement Microsoft Office** , puis choisissez le bouton **Mettre à jour** .

- Assurez-vous que vous n’exécutez pas une version d’Office qui a été remis par démarrer en un clic. Consultez [Guide pratique pour Vérifier si Outlook est une application démarrer en un clic sur un ordinateur](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Assurez-vous que vous exécutez qu’une seule version de Microsoft Office.

Si vous continuez à rencontrer des problèmes, consultez [prise en charge supplémentaire pour les erreurs dans les solutions Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Voir aussi

[Prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Guide pratique pour Configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Guide pratique pour Installer Visual Studio Tools pour Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Guide pratique pour Installer les assemblys PIA Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md)
