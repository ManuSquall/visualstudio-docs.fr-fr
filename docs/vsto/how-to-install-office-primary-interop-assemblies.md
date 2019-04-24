---
title: 'Procédure : Installer les assemblys PIA Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2ddba23ecb6007ff3b678932b118208742d1f0d4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109502"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Procédure : Installer les assemblys PIA Office
  Installez les assemblys PIA (Primary Interop Assembly) Microsoft Office lorsque vous installez Office.

## <a name="to-install-the-pias-when-you-install-office"></a>Pour installer les assemblys PIA lors de l'installation de Microsoft Office

1. Assurez-vous que vous disposez d'une version du .NET Framework qui n'est pas antérieure à 2.0.

2. Installez Microsoft Office et assurez-vous que le **prise en charge de la programmabilité .NET** fonctionnalité est sélectionnée pour les applications que vous souhaitez étendre (cette fonctionnalité est incluse dans l’installation par défaut).

    > [!WARNING]
    >  Par défaut, les assemblys PIA est incorporés dans votre solution lorsque vous le générez sans que vous ayez à distribuer aux utilisateurs en tant que condition préalable à l’utilisation de votre complément VSTO ou la personnalisation.

## <a name="see-also"></a>Voir aussi
- [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)
- [Guide pratique pour Cibler les applications Office via les assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Guide pratique pour Configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Guide pratique pour Installer Visual Studio Tools pour Office runtime redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
