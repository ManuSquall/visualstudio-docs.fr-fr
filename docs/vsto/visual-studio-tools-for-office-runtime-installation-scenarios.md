---
title: Visual Studio Tools pour les scénarios d’installation d’Office Runtime
description: Découvrez comment vous pouvez installer Visual Studio 2010 Tools pour Office Runtime. Cet article décrit trois scénarios d’installation.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 671d8e929ebef1085f0bf2aedad2a3280c36514c
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448335"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools pour les scénarios d’installation d’Office Runtime

  Vous pouvez installer Visual Studio 2010 Tools pour Office Runtime de trois manières :

- quand vous installez Visual Studio ;

- quand vous installez Microsoft Office ;

- Quand vous installez Visual Studio 2010 Tools pour Office Runtime Redistributable.

  Les composants d'exécution qui sont installés dépendent de la configuration de l'ordinateur et du scénario d'installation.

## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Composants d’exécution installés dans chaque scénario d’installation

 Visual Studio 2010 Tools pour Office Runtime a trois composants : le chargeur de solution Office, les extensions Office pour le .NET Framework 3,5 et les extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Quand vous installez le runtime, le chargeur de solutions Office est systématiquement installé. L'installation des extensions Office pour le .NET Framework dépend de la configuration de l'ordinateur et du scénario d'installation. Si l’une des extensions Office ne peut pas être installée la première fois que le runtime est installé, le runtime installe automatiquement les extensions Office manquantes ultérieurement, quand certaines exigences sont remplies. Cette fonctionnalité du runtime est appelée *installer à la demande*.

 Le tableau suivant répertorie les composants du runtime qui sont installés par défaut dans chaque scénario d'installation du runtime. Vous trouverez plus d'informations sur chaque scénario plus loin dans cette rubrique.

|Scénario d'installation du runtime|Chargeur de solutions Office|Extensions Office pour le .NET Framework 3.5|Extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Extensions Office pour le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|
|-----------------------------------|----------------------------|--------------------------------------------------| - |---------------------------------------------------------------------------|
|Avec [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] et versions ultérieures|Oui|Oui, si le .NET Framework 3.5 est déjà installé.|Oui|Oui|
|Avec [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Oui|Oui, si le .NET Framework 3.5 est déjà installé.|Non|Non|
|Avec Office 2010 Service Pack 1 (SP1) ou version ultérieure|Oui|Oui, si le .NET Framework 3.5 est déjà installé.|Oui, si le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] est déjà installé.|Non|
|Avec Office 2013 et versions ultérieures|Oui|Oui, si le .NET Framework 3.5 est déjà installé.|Oui, si le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] est déjà installé.|Oui, si le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] est déjà installé.|
|Avec le composant redistribuable du runtime|Oui|Oui, si le .NET Framework 3.5 est déjà installé.|Oui, si le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] est déjà installé.|Oui, si le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] est déjà installé.|

### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Installez le runtime à l’aide de Visual Studio ou du Outils de développement Microsoft Office pour Visual Studio

 Quand vous installez les Outils de développement Office dans Visual Studio, les extensions Office pour le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] et le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sont systématiquement installés sur l'ordinateur de développement. Les extensions Office pour le .NET Framework 3.5 sont uniquement installées si le .NET Framework 3.5 est déjà installé sur l'ordinateur de développement. Si vous installez le .NET Framework 3.5 après avoir installé [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], le runtime installe automatiquement les extensions Office pour le .NET Framework 3.5 la première fois que vous créez un projet Office ciblant le .NET Framework 3.5.

> [!WARNING]
> Vous ne pouvez pas créer un projet Office qui cible le .NET Framework 3.5 à l'aide de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] ou version ultérieure.

 Pour plus d’informations sur l’installation des outils de développement Office, consultez [Comment : configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

### <a name="install-the-runtime-with-office"></a>Installer le Runtime avec Office

 Quand vous installez Office, les extensions Office pour le .NET Framework 3.5 sont installées si le .NET Framework 3.5 est déjà présent sur l'ordinateur. Si vous installez le .NET Framework 3.5 après Office, le runtime installe automatiquement les extensions Office pour le .NET Framework 3.5 la première fois qu’une application Office tente de charger une solution ciblant le .NET Framework 3.5.

 Les extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure sont également installées avec Office si les versions correspondantes du .NET Framework sont déjà présentes sur l’ordinateur.

 Pour vous assurer que vos utilisateurs disposent des extensions nécessaires à l’utilisation de votre application, incluez la dernière version de Visual Studio 2010 Tools pour Office Runtime Redistributable comme condition préalable pour votre solution. Pour plus d’informations sur les conditions préalables requises, consultez [conditions préalables pour la solution Office pour le déploiement](/previous-versions/bb608617(v=vs.110)).

### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Installer le runtime à l’aide du package redistribuable du Runtime

 Vous pouvez installer le runtime en exécutant Visual Studio 2010 Tools pour Office Runtime Redistributable manuellement ou en incluant le package redistribuable comme condition préalable lors du déploiement d’une solution Office.

 Quand vous installez le runtime à l’aide du package redistribuable Visual Studio 2010 Tools pour Office Runtime, les extensions Office pour le .NET Framework 3,5 et les extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure sont installées si les versions correspondantes du .NET Framework sont déjà présentes sur l’ordinateur. Si l’une de ces versions du .NET Framework ne se trouve pas sur l’ordinateur lors de l’installation du runtime, les extensions Office pour la version du .NET Framework manquante ne sont pas installées à ce stade. Si vous décidez d’installer la version manquante du .NET Framework par la suite, le runtime installe automatiquement les extensions Office correspondantes à la prochaine installation d’une solution nécessitant ces extensions (si le runtime a été installé avec une solution déployée à l’aide de ClickOnce) ou au prochain chargement d’une telle solution (si le runtime a été installé avec une solution déployée à l’aide de Windows Installer).

 Pour plus d’informations sur l’inclusion des conditions préalables dans une solution ClickOnce, consultez [procédure : installer les composants requis sur les ordinateurs des utilisateurs finaux pour exécuter des solutions Office](/previous-versions/bb608608(v=vs.110)). Pour plus d’informations sur l’installation manuelle du runtime à partir du package redistribuable, consultez [Comment : installer le Visual Studio Tools pour le package redistribuable Office Runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Assemblys dans le Visual Studio Tools pour Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
