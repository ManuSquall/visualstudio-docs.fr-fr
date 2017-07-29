---
title: "Installer et gérer un contenu local | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hv_manage
helpviewer_keywords:
- changing content installation source [Help Viewer 2.0]
- updating local content [Help Viewer 2.0]
- Help Viewer 2.0, content installation source
- Help Viewer 2.0, updating local content
- Help Viewer 2.0, changing content installation source
- installing local content [Help Viewer 2.0]
- content installation source [Help Viewer 2.0]
- downloading content [Help Viewer 2.0]
- removing local content [Help Viewer 2.0]
- Help Viewer 2.0, removing local content
- Help Viewer 2.0, installing local content
- Help Viewer 2.0, downloading content
ms.assetid: efd9df4c-2e69-4c50-992c-9678a8d8cf19
caps.latest.revision: 25
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: b016ce5c67f1aa7242d7af3f3fb1142b61145f63
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="install-and-manage-local-content"></a>Installer et gérer un contenu local
Microsoft Help Viewer vous permet d’ajouter, de supprimer, de mettre à jour et de déplacer le contenu d’aide installé sur votre ordinateur pour répondre à vos besoins de développement de logiciels.  
  
 Pour gérer le contenu sur votre ordinateur local, vous devez vous connecter avec un compte qui dispose des autorisations d'administration. Par ailleurs, vous ne pourrez peut-être pas gérer le contenu local si vous travaillez dans un environnement d'entreprise, car il est possible que les administrateurs système prennent ces décisions pour votre organisation. Pour plus d’informations, consultez le [Guide de l’administrateur de la visionneuse d’aide](../ide/help-viewer-administrator-guide.md).  
  
## <a name="changing-the-content-installation-source"></a>Modification de la source d'installation du contenu  
 Par défaut, la visionneuse d'aide installe le contenu à partir d'un service en ligne Microsoft. En règle générale, vous ne devez pas modifier votre source de contenu, sauf si vous travaillez dans un environnement d'entreprise et qu'un administrateur système a déjà installé du contenu dans un autre emplacement.  
  
#### <a name="to-change-the-content-installation-source"></a>Pour modifier la source d'installation du contenu  
  
1.  Sous l’onglet **Gérer le contenu**, sélectionnez la case d’option **Disque**.  
  
    > [!NOTE]
    >  L’option **Disque** n’est pas disponible si votre administrateur ne vous a pas autorisé à modifier la source d’installation du contenu. Pour plus d’informations, consultez le [Guide de l’administrateur de la visionneuse d’aide](../ide/help-viewer-administrator-guide.md).  
  
2.  Effectuez l’une des opérations suivantes :  
  
    -   Entrez le chemin d’un fichier .msha ou l’URL d’un point de terminaison de service.  
  
    -   Choisissez le bouton de navigation (**...**) pour accéder à un fichier .msha.  
  
    -   Dans la liste, choisissez la dernière entrée utilisée.  
  
## <a name="download-and-install-content-locally"></a>Télécharger et installer le contenu localement  
 Vous pouvez afficher les rubriques sans connexion Internet si vous téléchargez et installez le contenu sur votre ordinateur local.  
  
> [!IMPORTANT]
>  Pour installer le contenu, vous devez vous connecter avec un compte qui dispose des autorisations d'administration.  
  
 Si l'IDE de Visual Studio est définie sur une langue autre que l'anglais, vous pouvez installer le contenu en anglais, le contenu localisé ou les deux. Toutefois, aucun contenu ne s’affiche si vous installez uniquement la version anglaise et que la case **Inclure le contenu en anglais dans tous les onglets de navigation et l’aide demandée via la touche F1** est décochée dans la boîte de dialogue **Options de la visionneuse**.  
  
#### <a name="to-download-and-install-content"></a>Pour télécharger et installer du contenu  
  
1.  Choisissez l’onglet **Gérer le contenu**.  
  
2.  Dans la liste de contenu, choisissez le lien **Ajouter** à côté du ou des livres que vous voulez télécharger et installer.  
  
     Le livre est ajouté à la liste **Modifications en attente** et la taille estimée du ou des livres spécifiés apparaît sous cette liste. Certains livres partagent des rubriques, la taille totale du téléchargement de plusieurs livres peut être inférieure à la somme de la taille de chaque livre spécifié.  
  
3.  Choisissez le bouton **Mettre à jour**.  
  
     Le ou les livres que vous avez spécifiés sont installés avec les éventuelles mises à jour des livres dont vous disposez déjà sur votre ordinateur. La durée d'installation varie, mais vous pouvez observer la progression dans la barre d'état.  
  
## <a name="removing-local-content"></a>Suppression du contenu local  
 Vous pouvez économiser de l'espace disque en supprimant le contenu indésirable de votre ordinateur.  
  
> [!IMPORTANT]
>  Vous devez disposer des autorisations d'administration pour supprimer du contenu.  
  
 Aucun contenu ne s’affiche si l’IDE de Visual Studio est défini sur une langue autre que l’anglais, que vous supprimez le contenu localisé et que la case **Inclure le contenu en anglais dans tous les onglets de navigation et l’aide demandée via la touche F1** est décochée dans la boîte de dialogue **Options de la visionneuse**.  
  
#### <a name="to-remove-content"></a>Pour supprimer du contenu  
  
1.  Choisissez l’onglet **Gérer le contenu**.  
  
2.  Dans la liste de contenu, choisissez le lien **Supprimer** à côté du ou des livres que vous voulez supprimer.  
  
     Le livre est ajouté à la liste **Modifications en attente**.  
  
3.  Choisissez le bouton **Mettre à jour**.  
  
     Le ou les livres spécifiés sont supprimés de votre ordinateur.  
  
## <a name="updating-local-content"></a>Mise à jour du contenu local  
 La barre d'état indique si des mises à jour de votre contenu installé sont disponibles.  
  
> [!IMPORTANT]
>  Si vous voulez que la visionneuse d’aide recherche automatiquement les mises à jour en ligne, vous devez ouvrir la boîte de dialogue **Options de la visionneuse**, puis cocher la case **Rechercher les mises à jour de contenu en ligne**.  
  
#### <a name="to-update-local-content"></a>Pour mettre à jour le contenu local  
  
-   En bas à droite de la barre d’état, choisissez le lien **Cliquez ici pour télécharger**.  
  
 La durée de la mise à jour varie, mais vous pouvez observer la progression dans la barre d'état.  
  
## <a name="moving-local-content"></a>Déplacement du contenu local  
 Vous pouvez économiser de l'espace disque en déplaçant le contenu installé sur votre ordinateur local vers un partage réseau ou une autre partition de votre ordinateur local.  
  
> [!IMPORTANT]
>  Pour déplacer le contenu, vous devez vous connecter avec un compte qui dispose des autorisations d'administration.  
  
#### <a name="to-move-local-content"></a>Pour déplacer du contenu local  
  
1.  Sous l’onglet **Gérer le contenu**, choisissez le bouton **Déplacer** sous **Chemin d’accès au stockage local**.  
  
     La boîte de dialogue **Déplacer le contenu** s’ouvre.  
  
2.  Dans la zone de texte **Vers**, entrez un autre emplacement pour le contenu, puis choisissez le bouton **OK**.  
  
3.  Choisissez le bouton **Fermer** une fois que le contenu a été déplacé.  
  
## <a name="see-also"></a>Voir aussi  
 [Visionneuse d’aide Microsoft 2.2](../ide/microsoft-help-viewer.md)
