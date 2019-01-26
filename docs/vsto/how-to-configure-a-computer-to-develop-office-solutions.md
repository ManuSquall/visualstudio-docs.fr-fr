---
title: 'Procédure : Configurer un ordinateur pour développer des solutions Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99dd7bea33fa534be8dceb0fb888ac50e23cd01d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865587"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Procédure : Configurer un ordinateur pour développer des solutions Office
  Pour configurer un ordinateur de développement de manière à pouvoir utiliser les Outils de développement Microsoft Office dans Visual Studio, suivez les instructions de cette rubrique. Vous devez détenir des privilèges d'administrateur sur l'ordinateur de développement pour effectuer ces étapes.  
  
### <a name="to-configure-the-development-computer"></a>Pour configurer l'ordinateur de développement  
  
1.  Installez une version de Visual Studio qui inclut les Outils de développement Office. Les Outils de développement Microsoft Office sont installés par défaut. Si vous personnalisez l’installation de Visual Studio en sélectionnant les fonctionnalités à installer, assurez-vous que **Microsoft Office Developer Tools** est sélectionné pendant l’installation. Pour plus d’informations sur les versions de Visual Studio qui incluent les outils de développement Office, consultez [configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
2.  Installez une version d'Office prise en charge par les Outils de développement Office dans Visual Studio. Pour plus d’informations, consultez [configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
     Assurez-vous également d'installer les assemblys PIA pour la version d'Office que vous installez. Les assemblys PIA sont installés avec Office par défaut. Si vous modifiez le programme d’installation Office, assurez-vous que le **prise en charge de la programmabilité .NET** fonctionnalité est sélectionnée pour les applications que vous souhaitez cibler.  
  
3.  Si vous avez une version anglaise de Visual Studio mais que vous utilisez des paramètres non anglais pour Windows, vous pouvez installer le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] linguistique pour voir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] messages dans la même langue que Windows. Les versions non anglaises de Visual Studio installent automatiquement le module linguistique. Le module linguistique est disponible à partir de la [centre de téléchargement Microsoft](http://go.microsoft.com/fwlink/?LinkId=140386).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles sont les nouveautés dans le développement Office](https://msdn.microsoft.com/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Guide pratique pour Installer Visual Studio Tools pour Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Guide pratique pour Installer les assemblys PIA Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
