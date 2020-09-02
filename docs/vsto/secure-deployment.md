---
title: Déploiement sécurisé
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1000504ad83706bd028af4bd668da7483e478b7a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62978370"
---
# <a name="secure-deployment"></a>Déploiement sécurisé
  Lorsque vous créez une solution Office, votre ordinateur de développement est automatiquement mis à jour pour permettre l’exécution du code de votre projet. Toutefois, lorsque vous déployez votre solution, vous devez fournir une preuve sur laquelle baser une décision d’approbation en signant la solution à l’aide d’un certificat ou de la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation. Pour plus d’informations, consultez accorder un niveau [de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Pour les personnalisations au niveau du document, si vous déployez le document sur un emplacement réseau, vous devez également ajouter l’emplacement du document à la liste des emplacements approuvés dans le centre de gestion de la confidentialité de l’application Office. Pour plus d’informations sur la définition des autorisations de document sur les ordinateurs des utilisateurs finaux, consultez [accorder une confiance aux documents](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Empêcher l’exécution de code dans les solutions Office
 Les administrateurs peuvent utiliser le registre pour empêcher l’exécution de toutes les solutions Office sur un ordinateur. Quand une solution Office avec des extensions de code managé est ouverte, le Visual Studio Tools pour Office Runtime vérifie s’il existe une entrée portant le nom `Disabled` sous l’une des clés de Registre suivantes sur l’ordinateur :

- **HKEY_CURRENT_USER \Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE \Software\Microsoft\VSTO**

  Pour empêcher les solutions Office d’exécuter du code, créez une `Disabled` entrée sous l’une ou les deux clés de Registre, puis spécifiez l’un des types de données et valeurs suivants pour `Disabled` :

- REG_SZ ou REG_EXPAND_SZ défini sur une chaîne autre que « 0 » (zéro).

- REG_DWORD défini sur une valeur autre que 0 (zéro).

  Pour permettre aux solutions Office d’exécuter du code, affectez à ces deux entrées la valeur `Disabled` 0 (zéro) ou supprimez les entrées de registre.

## <a name="see-also"></a>Voir aussi
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Préparer les ordinateurs à exécuter ou à héberger des solutions Office](https://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
