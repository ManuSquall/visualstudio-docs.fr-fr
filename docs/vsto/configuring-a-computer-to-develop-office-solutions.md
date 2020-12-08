---
title: Configurer un ordinateur pour développer des solutions Office
description: Découvrez comment vous pouvez installer une version prise en charge de Visual Studio, la .NET Framework et Microsoft Office afin de pouvoir créer des personnalisations et des compléments VSTO pour Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3658f655c50c9d1a0775a8cc69dd65baf32d1408
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847258"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurer un ordinateur pour développer des solutions Office

Pour créer des compléments VSTO et des personnalisations pour Microsoft Office, installez une version prise en charge de Visual Studio, le .NET Framework et Microsoft Office.

|Logiciel|Versions prises en charge|
|--------------|------------------------|
|Visual Studio 2017| Toute édition avec la charge de travail **développement Office/SharePoint** .|
|.NET Framework|-Le .NET Framework 4 ou version ultérieure.|
|Microsoft Office|<ul><li>Toute édition de la suite d’Office, y compris les applications Microsoft 365 pour l’entreprise.</li><li>N'importe laquelle des applications autonomes suivantes :<br /><br /> <ul><li>Excel</li><li>InfoPath (Office 2013 et Office 2010 uniquement)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic pour Applications (VBA) doit être installé dans le cadre d'Office. **Important :** Les versions « démarrer en un clic » des applications Office 2010 ne sont pas prises en charge.|

Pour obtenir des instructions détaillées sur l’installation, consultez [Comment : configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Si les modèles de projet n’apparaissent pas ou ne fonctionnent pas dans Visual Studio

Si vous installez une version prise en charge de Visual Studio, les .NET Framework et Microsoft Office, mais que les modèles de projet Office n’apparaissent pas dans la boîte de dialogue **nouveau projet** de Visual Studio, ou si vous recevez une erreur lorsque vous essayez d’en utiliser un, vérifiez les éléments suivants :

- Assurez-vous que les outils de développement Microsoft Office sont installés sur votre ordinateur.

     Les outils de développement Office sont un composant facultatif de Visual Studio, mais ils sont installés automatiquement avec Visual Studio. Si vous personnalisez l'installation de Visual Studio en spécifiant les fonctionnalités à installer, assurez-vous de choisir **Outils de développement Microsoft Office** pendant l'installation, afin d'installer ces outils.

     Pour vous assurer que ces outils sont installés, démarrez le programme d’installation de Visual Studio, puis choisissez le bouton **modifier** . Cochez la case **Outils de développement Microsoft Office** , puis choisissez le bouton **Mettre à jour** .

- Assurez-vous que vous n’exécutez pas une version d’Office qui a été fournie par une exécution « démarrer en un clic ». Consultez [procédure : vérifier si Outlook est une application « démarrer en un clic » sur un ordinateur](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Assurez-vous que vous n’exécutez qu’une seule version de Microsoft Office.

Si vous continuez à rencontrer des problèmes, consultez [prise en charge supplémentaire des erreurs dans les solutions Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Voir aussi
- [Prise en main &#40;le développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Comment : configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Comment : installer le Visual Studio Tools pour le package redistribuable Office Runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Comment : installer les assemblys PIA (Primary Interop Assembly) Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md)