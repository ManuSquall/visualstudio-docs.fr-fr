---
title: 'Comment : signer des solutions Office'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 23afc171fd97620b3e6801b8d199da6890198d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545754"
---
# <a name="how-to-sign-office-solutions"></a>Comment : signer des solutions Office
  Si vous signez une solution, vous pouvez accorder la confiance à la solution en utilisant le certificat comme preuve. Vous pouvez utiliser le même certificat pour plusieurs solutions, et toutes les solutions seront approuvées sans aucune mise à jour de stratégie de sécurité supplémentaire.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Si vous modifiez manuellement les manifestes d’application et de déploiement à l’aide de l’Outil Manifest Generation and Editing (*mage.exe* et *mageui.exe*), vous devez signer à nouveau les manifestes avant de pouvoir les utiliser. Pour plus d’informations, consultez [Comment : signer à nouveau les manifestes d’application et de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Signer à l’aide d’un certificat
 Un certificat est un fichier qui contient une clé unique et l’identité de l’éditeur de la solution. Vous pouvez acheter des certificats auprès d’une autorité de certification, ou créer votre propre certificat et demander à une autorité de certification de le signer.

 Visual Studio signe les solutions Office avec un certificat temporaire pour activer le débogage. Vous ne devez pas utiliser le certificat temporaire dans les solutions déployées comme preuve.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Pour signer une solution Office à l’aide d’un certificat

1. Dans le menu **projet** , cliquez sur**Propriétés**de _NomSolution_.

2. Cliquez sur l'onglet **Signature** .

3. Sélectionnez **signer les manifestes ClickOnce**.

4. Localisez le certificat en cliquant sur **Sélectionner dans le Store** ou **Sélectionner dans un fichier** et en accédant au certificat.

5. Pour vérifier que le certificat correct est utilisé, cliquez sur **plus de détails** pour afficher les informations du certificat.

## <a name="see-also"></a>Voir aussi

- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
- [Accorder un niveau de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)
- [Page Signature, Concepteur de projets](../ide/reference/signing-page-project-designer.md)
