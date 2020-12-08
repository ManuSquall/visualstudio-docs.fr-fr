---
title: 'Comment : installer les assemblys PIA (Primary Interop Assembly) Office'
description: Découvrez comment installer les assemblys PIA (Primary Interop Assembly) Microsoft Office lorsque vous installez Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
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
ms.openlocfilehash: 15a55650f2e4a434343c9128cc8f28117b54288e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845880"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Comment : installer les assemblys PIA (Primary Interop Assembly) Office
  Installez les assemblys PIA (Primary Interop Assembly) Microsoft Office lorsque vous installez Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Pour installer les assemblys PIA lors de l'installation de Microsoft Office

1. Assurez-vous que vous disposez d'une version du .NET Framework qui n'est pas antérieure à 2.0.

2. Installez Microsoft Office et assurez-vous que la fonctionnalité **prise en charge de la programmabilité .net** est sélectionnée pour les applications que vous souhaitez étendre (cette fonctionnalité est incluse dans l’installation par défaut).

    > [!WARNING]
    > Par défaut, les assemblys PIA sont incorporés dans votre solution lorsque vous les générez, de sorte que vous n’avez pas à distribuer les assemblys PIA aux utilisateurs comme condition préalable à l’utilisation de votre complément VSTO ou de la personnalisation.

## <a name="see-also"></a>Voir aussi
- [Assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md)
- [Comment : cibler des applications Office par le biais d’assemblys PIA](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Comment : configurer un ordinateur pour développer des solutions Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Comment : installer le Visual Studio Tools pour le package redistribuable Office Runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Vue d’ensemble du développement de solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Prise en main &#40;le développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
