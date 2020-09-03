---
title: 'Comment : afficher l’onglet Développeur sur le ruban'
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 41070c92d0c27c1ee8fbf480f7461c22421b8fdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545845"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Comment : afficher l’onglet Développeur sur le ruban
  Pour accéder à l’onglet **développeur** sur le ruban d’une application Office, vous devez le configurer pour afficher cet onglet, car il n’apparaît pas par défaut. Par exemple, vous devez afficher cet onglet pour ajouter un <xref:Microsoft.Office.Tools.Word.GroupContentControl> à une personnalisation au niveau du document pour Word.

> [!NOTE]
> Ces informations d'aide s'appliquent uniquement aux applications Office 2010 ou version ultérieure. Si vous souhaitez afficher cet onglet dans le système 2007 Microsoft Office, consultez la version suivante de cette rubrique [Comment : afficher l’onglet Développeur sur le ruban](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> L’accès n’a pas d’onglet **développeur** .

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Pour afficher l'onglet Développeur

1. Démarrez l'une des applications Office prises en charge dans cette rubrique. Consultez la Remarque **s’applique à :** plus haut dans cette rubrique.

2. Sous l’onglet **fichier** , choisissez le bouton **options** .

     L’illustration suivante montre l’onglet **fichier** et le bouton **Options** dans Office 2010.

     ![Choix de fichier, Options dans Outlook 2010](../vsto/media/vsto-office-file-tab.png "Choix de fichier, Options dans Outlook 2010")

     L’illustration suivante montre l’onglet **fichier** dans Office 2013.

     ![Onglet Fichier dans Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Onglet Fichier dans Outlook 2013")

     L’illustration suivante montre le bouton **options** dans Office 2013.

     ![Bouton Options dans Outlook 2013 Preview](../vsto/media/vsto-office2013-optionsbutton.png "Bouton Options dans Outlook 2013 Preview")

3. Dans la boîte de dialogue**options** de _applicationName_, choisissez le bouton **personnaliser le ruban** .

     L’illustration suivante montre la boîte de dialogue **options** et le bouton **personnaliser le ruban** dans Excel 2010. L'emplacement de ce bouton est similaire dans toutes les autres applications répertoriées dans la section « S'applique à » au début de cette rubrique.

     ![Bouton Personnaliser le Ruban](../vsto/media/vsto-office2010-customizeribbonbutton.png "Bouton Personnaliser le Ruban")

4. Dans la liste des onglets principaux, activez la case à cocher **développeur** .

     L’illustration suivante montre la case à cocher **développeur** dans Word 2010 et [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . L'emplacement de cette case à cocher est similaire dans toutes les autres applications répertoriées dans la section « S'applique à » au début de cette rubrique.

     ![Case à cocher « Développeur » dans la boîte de dialogue Options Word](../vsto/media/vsto-office2010-developercheckbox.png "Case à cocher « Développeur » dans la boîte de dialogue Options Word")

5. Choisissez le bouton **OK** pour fermer la boîte de dialogue **options** .

## <a name="see-also"></a>Voir aussi
- [Personnalisation de l’interface utilisateur Office](../vsto/office-ui-customization.md)
