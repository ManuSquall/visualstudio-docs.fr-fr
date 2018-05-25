---
title: L’impact de cette fonctionnalité sur les solutions Office
ms.custom: ''
ms.date: 07/20/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- autosave
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 21c49599ddc992bf35e6c1464b664a23fb33a691
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
---
# <a name="how-autosave-impacts-office-solutions"></a>L’impact de cette fonctionnalité sur les solutions Office

Cette fonctionnalité est une fonctionnalité pour Excel, PowerPoint et Word qui, lorsque activé, permet des modifications de l’utilisateur à enregistrer automatiquement et en continu. Si cette fonctionnalité est désactivée, puis enregistrer doit être déclenchée manuellement pour la conservation des modifications de l’utilisateur. Avec l’ajout de cette fonctionnalité, vous devrez peut-être effectuer des ajustements à votre solution Office afin de vous assurer qu’il fonctionne correctement même alors que l’enregistrement automatique. Pour plus d’informations, consultez [comment cette fonctionnalité a un impact sur les compléments et les macros](https://msdn.microsoft.com/vba/office-shared-vba/articles/how-autosave-impacts-addins-and-macros). Pour plus d’informations sur cette fonctionnalité en général, consultez [quel est l’enregistrement automatique ?](https://support.office.com/en-US/article/What-is-AutoSave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5).

Remarque : Cette fonctionnalité pour Windows Desktop Word, Excel et PowerPoint a été introduite dans 2017 et n’est actuellement disponible pour les abonnés d’Office 365. Les utilisateurs qui ont acheté une licence définitive pour Office 2016 ou une version antérieure n’ont pas actuellement accès à la fonction cocréation. (Excel Online, Excel pour Android, Excel pour iOS et Excel Mobile dans le Windows Store prennent également en charge cette fonctionnalité). 

## <a name="see-also"></a>Voir aussi
[Développer des solutions Office](./developing-office-solutions.md)
