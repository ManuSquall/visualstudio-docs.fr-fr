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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56604923"
---
# <a name="secure-deployment"></a>Déploiement sécurisé
  Lorsque vous créez une solution Office, votre ordinateur de développement est automatiquement mis à jour pour permettre au code dans votre projet doit être exécuté. Toutefois, lorsque vous déployez votre solution, vous devez fournir la preuve sur laquelle baser la décision d’approbation par la solution avec un certificat de signature, ou à l’aide de la [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] clé d’invite d’approbation. Pour plus d’informations, consultez [accorder une confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Pour les personnalisations au niveau du document, si vous déployez le document vers un emplacement réseau, vous devez également ajouter l’emplacement du document à la liste des emplacements approuvés dans le centre de confidentialité de l’application Office. Pour plus d’informations sur la façon de définir les autorisations du document sur les ordinateurs des utilisateurs finaux, consultez [accorder une confiance aux documents](../vsto/granting-trust-to-documents.md).

## <a name="prevent-office-solutions-from-running-code"></a>Empêcher l’exécution de code des solutions Office
 Les administrateurs peuvent utiliser le Registre pour empêcher que toutes les solutions Office en cours d’exécution sur un ordinateur. Lorsqu’une solution Office qui a des extensions de code managé est ouvert, Visual Studio Tools pour les vérifications à l’exécution Office si une entrée avec le nom `Disabled` existe sous une des clés de Registre suivantes sur l’ordinateur :

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  Pour empêcher les solutions Office à partir de l’exécution de code, créez un `Disabled` entrée sous un ou deux de ces clés de Registre et spécifiez l’une des valeurs pour les types de données suivants `Disabled`:

- REG_SZ ou REG_EXPAND_SZ est définie sur n’importe quelle chaîne autre que « 0 » (zéro).

- REG_DWORD qui est définie sur n’importe quelle valeur autre que 0 (zéro).

  Pour activer les solutions Office exécuter du code, définissez à la fois de la `Disabled` entrées à 0 (zéro), ou supprimer les entrées de Registre.

## <a name="see-also"></a>Voir aussi
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
- [Préparer les ordinateurs pour exécuter ou héberger des solutions Office](https://msdn.microsoft.com/be1b173f-7261-4d74-aa4e-94ccd43db8d8)
- [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)
