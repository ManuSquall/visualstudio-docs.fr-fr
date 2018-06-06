---
title: Visual Studio Tools pour les scénarios d’installation Office runtime
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, installation scenarios
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2af3f4834fecfe4fcfba30f736892057893ed143
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767723"
---
# <a name="visual-studio-tools-for-office-runtime-installation-scenarios"></a>Visual Studio Tools pour les scénarios d’installation Office runtime
  Vous pouvez installer Visual Studio 2010 Tools pour Office runtime de trois façons :  
  
-   quand vous installez Visual Studio ;  
  
-   quand vous installez Microsoft Office ;  
  
-   Lorsque vous installez Visual Studio 2010 Tools pour Office runtime redistributable.  
  
 Les composants d'exécution qui sont installés dépendent de la configuration de l'ordinateur et du scénario d'installation.  
  
## <a name="runtime-components-that-are-installed-in-each-installation-scenario"></a>Composants d’exécution qui sont installés dans chaque scénario d’installation  
 Visual Studio 2010 Tools pour Office runtime comprend trois composants : le chargeur de solutions Office, les extensions Office pour .NET Framework 3.5 et les extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Quand vous installez le runtime, le chargeur de solutions Office est systématiquement installé. L'installation des extensions Office pour le .NET Framework dépend de la configuration de l'ordinateur et du scénario d'installation. Si l’une des extensions Office ne peut pas être installée la première fois que le runtime est installé, le runtime installe automatiquement les extensions Office manquantes ultérieurement, quand certaines exigences sont remplies. Cette fonctionnalité du runtime est appelée *installer à la demande*.  
  
 Le tableau suivant répertorie les composants du runtime qui sont installés par défaut dans chaque scénario d'installation du runtime. Vous trouverez plus d'informations sur chaque scénario plus loin dans cette rubrique.  
  
|Scénario d'installation du runtime|Chargeur de solutions Office|Extensions Office pour le .NET Framework 3.5|Extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]|Extensions Office pour le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]|  
|-----------------------------------|----------------------------|--------------------------------------------------|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Avec [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] et versions ultérieures|Oui|Oui, si le .NET Framework 3.5 est déjà installé.|Oui|Oui|  
|Avec [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Oui|Oui, si le .NET Framework 3.5 est déjà installé.|Non|Non|  
|Avec Office 2010 Service Pack 1 (SP1) ou version ultérieure|Oui|Oui, si le .NET Framework 3.5 est déjà installé.|Oui, si le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] est déjà installé.|Non|  
|Avec le composant redistribuable du runtime|Oui|Oui, si le .NET Framework 3.5 est déjà installé.|Oui, si le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] est déjà installé.|Oui, si le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] est déjà installé.|  
  
### <a name="install-the-runtime-with-visual-studio-or-the-microsoft-office-developer-tools-for-visual-studio"></a>Installez le runtime avec Visual Studio ou les outils de développement Microsoft Office pour Visual Studio  
 Quand vous installez les Outils de développement Office dans Visual Studio, les extensions Office pour le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] et le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sont systématiquement installés sur l'ordinateur de développement. Les extensions Office pour le .NET Framework 3.5 sont uniquement installées si le .NET Framework 3.5 est déjà installé sur l'ordinateur de développement. Si vous installez le .NET Framework 3.5 après avoir installé [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], le runtime installe automatiquement les extensions Office pour le .NET Framework 3.5 la première fois que vous créez un projet Office ciblant le .NET Framework 3.5.  
  
> [!WARNING]  
>  Vous ne pouvez pas créer un projet Office qui cible le .NET Framework 3.5 à l'aide de [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] ou version ultérieure.  
  
 Pour plus d’informations sur la façon d’installer les outils de développement Office, consultez [Comment : configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
### <a name="install-the-runtime-with-office"></a>Installez le runtime avec Office  
 Quand vous installez Office, les extensions Office pour le .NET Framework 3.5 sont installées si le .NET Framework 3.5 est déjà présent sur l’ordinateur. Si vous installez le .NET Framework 3.5 après Office, le runtime installe automatiquement les extensions Office pour le .NET Framework 3.5 la première fois qu'une application Office tente de charger une solution ciblant le .NET Framework 3.5.  
  
 Les extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure ne sont pas installées avec Office, même si le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure est déjà présent quand vous installez Office.  
  
 Les extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] sont installées avec Office. Les utilisateurs finaux peuvent obtenir les extensions Office pour le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] en installant une mise à jour de Windows.  
  
 Pour vous assurer que vos utilisateurs ont les extensions nécessaires pour utiliser votre application, incluez la version la plus récente de Visual Studio 2010 Tools pour Office runtime redistributable comme condition préalable pour votre solution. Pour plus d’informations sur la configuration requise, consultez [conditions de solution Office pour le déploiement](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e).  
  
### <a name="install-the-runtime-by-using-the-runtime-redistributable"></a>Installez le runtime à l’aide du package redistribuable du runtime  
 Vous pouvez installer le runtime en exécutant Visual Studio 2010 Tools pour Office runtime redistributable manuellement ou en incluant le composant redistribuable comme composant requis lorsque vous déployez une solution Office.  
  
 Lorsque vous installez le runtime à l’aide de Visual Studio 2010 Tools pour Office runtime redistributable, les extensions Office pour .NET Framework 3.5 et les extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure sont installées si les versions correspondantes du .NET Framework Framework sont déjà présents sur l’ordinateur. Si l’une de ces versions du .NET Framework ne se trouve pas sur l’ordinateur lors de l’installation du runtime, les extensions Office pour la version du .NET Framework manquante ne sont pas installées à ce stade. Si vous décidez d’installer la version manquante du .NET Framework par la suite, le runtime installe automatiquement les extensions Office correspondantes à la prochaine installation d’une solution nécessitant ces extensions (si le runtime a été installé avec une solution déployée à l’aide de ClickOnce) ou au prochain chargement d’une telle solution (si le runtime a été installé avec une solution déployée à l’aide de Windows Installer).  
  
 Pour plus d’informations sur l’inclusion de conditions préalables dans une solution ClickOnce, consultez [Comment : installer les composants requis sur les ordinateurs des utilisateurs finaux pour exécuter des solutions Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98). Pour plus d’informations sur la façon d’installer le package redistribuable manuellement, consultez [Comment : installer Visual Studio Tools pour Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Visual Studio Tools pour Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Assemblys dans Visual Studio Tools pour Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)  
  
  