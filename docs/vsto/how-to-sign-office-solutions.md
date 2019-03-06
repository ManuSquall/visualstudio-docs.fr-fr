---
title: 'Procédure : Signer des solutions Office'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 25c5388c1b1d14efad9e76b2494f8da423d28979
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871661"
---
# <a name="how-to-sign-office-solutions"></a>Procédure : Signer des solutions Office
  Si vous vous connectez à une solution, vous pouvez accorder une confiance à la solution en utilisant le certificat en tant que preuve. Vous pouvez utiliser le même certificat pour plusieurs solutions, et toutes les solutions seront approuvées avec aucune mise à jour de stratégie de sécurité supplémentaire.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Si vous modifiez manuellement l’application et manifestes de déploiement à l’aide de la Manifest Generation and Editing Tool (*mage.exe* et *mageui.exe*), vous devez resigner les manifestes avant de pouvoir les utiliser. Pour plus d'informations, voir [Procédure : Resigner des manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Se connecter à l’aide d’un certificat
 Un certificat est un fichier qui contient une clé unique et l’identité de l’éditeur de solutions. Vous pouvez acheter des certificats à partir d’une autorité de certification, ou créer votre propre certificat et avoir une autorité de certification signez-le.

 Visual Studio connecte avec un certificat temporaire pour activer le débogage des solutions Office. Vous ne devez pas utiliser le certificat temporaire dans des solutions déployées en tant que preuve.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Pour signer une solution Office à l’aide d’un certificat

1.  Sur le **projet** menu, cliquez sur _SolutionName_**propriétés**.

2.  Cliquez sur l’onglet **Signature**.

3.  Sélectionnez **signer les manifestes ClickOnce**.

4.  Recherchez le certificat en cliquant sur **sélectionner dans Store** ou **sélectionner à partir du fichier** et en accédant au certificat.

5.  Pour vérifier que le certificat approprié est utilisé, cliquez sur **plus de détails** pour afficher les informations de certificat.

## <a name="see-also"></a>Voir aussi

- [Sécurisez les solutions Office](../vsto/securing-office-solutions.md)
- [Accorder votre confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)
- [Page Signature, Concepteur de projet](../ide/reference/signing-page-project-designer.md)
