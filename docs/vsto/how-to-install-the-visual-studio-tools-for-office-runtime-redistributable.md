---
title: 'Procédure : Installer Visual Studio Tools pour Office runtime redistributable'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74e63f34a7285fc035ae2acd338a73725a77e6ce
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867206"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Procédure : Installer Visual Studio Tools pour Office runtime redistributable
  Visual Studio 2010 Tools pour Office runtime doit être installé sur chaque ordinateur qui exécute des solutions qui sont créées en utilisant les outils de développement Microsoft Office dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Le runtime est installé automatiquement quand vous installez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et Microsoft Office. Pour plus d’informations, consultez [Visual Studio Tools pour les scénarios d’installation Office runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 Dans les situations suivantes, vous devrez peut-être suivre les instructions d'installation manuelles ci-dessous :  
  
-   Vous devez installer [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sur un serveur. Par exemple, vous souhaitez utiliser la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour gérer des solutions au niveau du document sur un serveur.  
  
-   Vous devez installer le runtime sur un ordinateur sur lequel tous les autres composants requis pour les solutions Office sont déjà installés.  
  
    > [!NOTE]  
    >  Vous devez être administrateur de l'ordinateur de développement pour installer le .NET Framework et [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Pour installer Visual Studio Tools pour Office Runtime  
  
1.  Installez le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure.  
  
    -   Pour télécharger le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], consultez [Microsoft .NET Framework 4 (programme d’installation Web)](http://go.microsoft.com/fwlink/?LinkId=178957).  
  
    -   Pour télécharger le [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)], consultez [Microsoft .NET Framework 4 Client Profile (programme d’installation Web)](http://go.microsoft.com/fwlink/?LinkId=178958).  
  
    -   Pour télécharger le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], consultez [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).  
  
2.  Exécutez *vstor_redist.exe* pour installer le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
     Vous pouvez télécharger ces fichiers d’installation à partir de [Visual Studio 2010 Tools pour Office runtime](http://go.microsoft.com/fwlink/?LinkId=140384). Les composants requis pour [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] correspondent aux composants requis du .NET Framework.  
  
     La [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]inclut les modules linguistiques. Si votre installation de Windows est définie avec une autre langue que l'anglais, vous pouvez afficher les messages du runtime dans la même langue que celle de Windows. De même, si les utilisateurs finaux installent [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] et qu'ils exécutent ensuite vos solutions sur des installations Windows définies avec une autre langue que l'anglais, les messages du runtime apparaîtront dans la même langue que celle de Windows. Dans certains cas, vous pouvez avoir besoin de modules linguistiques supplémentaires. Par exemple, vous devrez peut-être les modules linguistiques supplémentaires si votre copie de Windows utilise plusieurs paramètres de langue, ou si vous basculez vers une autre langue, une fois que vous avez déjà installé le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Vous pouvez trouver des modules linguistiques [Microsoft Visual Studio 2010 Tools pour Microsoft Office system (runtime version 4.0) language pack](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [Guide pratique pour Configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Guide pratique pour Installer les assemblys PIA Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Déployer une solution Office](../vsto/deploying-an-office-solution.md)  
