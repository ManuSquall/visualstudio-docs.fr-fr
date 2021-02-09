---
title: 'Comment : installer le Visual Studio Tools pour le package redistribuable Office Runtime'
description: Découvrez comment vous pouvez installer le package redistribuable Microsoft Visual Studio 2010 Tools pour Office Runtime.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75dc5b2f3f207603320a773ebd71f5d6d3f81b8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918613"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Comment : installer le Visual Studio Tools pour le package redistribuable Office Runtime
  Visual Studio 2010 Tools pour Office Runtime doit être installé sur chaque ordinateur qui exécute des solutions créées à l’aide des outils de développement Microsoft Office dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Le runtime est installé automatiquement quand vous installez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] et Microsoft Office. Pour plus d’informations, consultez [Visual Studio Tools pour les scénarios d’installation d’Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Dans les situations suivantes, vous devrez peut-être suivre les instructions d'installation manuelles ci-dessous :

- Vous devez installer [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sur un serveur. Par exemple, vous souhaitez utiliser la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> pour gérer des solutions au niveau du document sur un serveur.

- Vous devez installer le runtime sur un ordinateur sur lequel tous les autres composants requis pour les solutions Office sont déjà installés.

    > [!NOTE]
    > Vous devez être administrateur de l'ordinateur de développement pour installer le .NET Framework et [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Pour installer Visual Studio Tools pour Office Runtime

1. Installez le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure.

    - Pour télécharger le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , consultez [Microsoft .NET Framework 4 (programme d’installation Web)](https://www.microsoft.com/download/details.aspx?id=17851).

    - Pour télécharger le [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] , consultez [Microsoft .NET Framework 4 Client Profile (programme d’installation Web)](https://www.microsoft.com/download/details.aspx?id=17113).

    - Pour télécharger le [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , consultez [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Exécutez *vstor_redist.exe* pour installer le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

     Vous pouvez télécharger ces fichiers d’installation à partir de [Visual Studio 2010 Tools pour Office Runtime](https://www.microsoft.com/download/details.aspx?id=56961). Les composants requis pour [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] correspondent aux composants requis du .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclut des modules linguistiques. Si votre installation de Windows est définie avec une autre langue que l'anglais, vous pouvez afficher les messages du runtime dans la même langue que celle de Windows. De même, si les utilisateurs finaux installent [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] et qu'ils exécutent ensuite vos solutions sur des installations Windows définies avec une autre langue que l'anglais, les messages du runtime apparaîtront dans la même langue que celle de Windows. Dans certains cas, vous pouvez avoir besoin de modules linguistiques supplémentaires. Par exemple, vous pouvez avoir besoin de modules linguistiques supplémentaires si votre copie de Windows utilise plusieurs paramètres de langue ou si vous basculez vers une autre langue une fois que vous avez déjà installé [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Des modules linguistiques sont disponibles à [l’adresse Microsoft Visual Studio 2010 Tools pour le module linguistique du système Microsoft Office (version 4,0 Runtime)](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Voir aussi
- [Prise en main &#40;le développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Comment : configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Comment : installer les assemblys PIA (Primary Interop Assembly) Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Gérer des documents sur un serveur à l’aide de la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
