---
title: 'Procédure : Installer les assemblys PIA (Primary Interop Assembly) Office'
ms.date: 08/14/2019
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
ms.openlocfilehash: ee6755a2d795d2018136785986a5a346ddc07dc6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551794"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Procédure : Installer les assemblys PIA (Primary Interop Assembly) Office
  Installez les assemblys PIA (Primary Interop Assembly) Microsoft Office lorsque vous installez Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Pour installer les assemblys PIA lors de l'installation de Microsoft Office

1. Assurez-vous que vous disposez d'une version du .NET Framework qui n'est pas antérieure à 2.0.

2. Installez Microsoft Office et assurez-vous que la fonctionnalité **prise en charge** de la programmabilité .net est sélectionnée pour les applications que vous souhaitez étendre (cette fonctionnalité est incluse dans l’installation par défaut).

    > [!WARNING]
    > Par défaut, les assemblys PIA sont incorporés dans votre solution lorsque vous les générez, de sorte que vous n’avez pas à distribuer les assemblys PIA aux utilisateurs comme condition préalable à l’utilisation de votre complément VSTO ou de la personnalisation.

## <a name="see-also"></a>Voir aussi
- [Assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md)
- [Guide pratique pour Cibler des applications Office par le biais d’assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Guide pratique pour Configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Guide pratique pour Installer le Visual Studio Tools pour le package redistribuable Office Runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Vue d’ensemble du &#40;développement des solutions Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Prise en &#40;main du développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
