---
title: 'Comment : réactiver un complément VSTO qui a été désactivé | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 25344d23e0c9f1d6d237d008b0f6b18372490d04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Comment : réactiver un complément VSTO qui a été désactivé
  Les applications Microsoft Office peuvent désactiver les compléments VSTO qui se comportent de façon inattendue. Si une application ne charge pas votre complément VSTO quand vous essayez de la déboguer, cela peut-être dû au fait qu'elle a désactivé votre complément VSTO de manière forcée ou en douceur.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="hard-disabled-vsto-add-ins"></a>Compléments VSTO désactivés de manière forcée  
 La désactivation de manière forcée peut se produire quand un complément VSTO entraîne la fermeture inattendue de l'application. Elle peut également se produire sur votre ordinateur de développement si vous arrêtez le débogueur pendant que le gestionnaire d'événements <xref:Microsoft.Office.Tools.AddIn.Startup> de votre complément VSTO est en cours d'exécution.  
  
#### <a name="to-re-enable-a-vsto-add-in"></a>Pour réactiver un complément VSTO  
  
1.  Dans l'application, cliquez sur l'onglet **Fichier** .  
  
2.  Cliquez sur le bouton *Options de* **nom_application** .  
  
3.  Dans le volet des catégories, cliquez sur **Compléments**.  
  
4.  Dans le volet d'informations, vérifiez que le complément VSTO apparaît dans la liste **Compléments d'applications désactivés** .  
  
     La colonne **Nom** indique le nom de l'assembly, et la colonne **Emplacement** indique le chemin d'accès complet du manifeste de l'application.  
  
5.  Dans la zone **Gérer** , cliquez sur **Éléments désactivés**, puis sur **Atteindre**.  
  
6.  Sélectionnez le complément VSTO, puis cliquez sur **Activer**.  
  
7.  Cliquez sur **Fermer**.  
  
## <a name="soft-disabled-vsto-add-ins"></a>Compléments VSTO désactivés en douceur  
 La désactivation en douceur peut se produire quand un complément VSTO génère une erreur qui n'entraîne pas la fermeture inattendue de l'application. Par exemple, une application peut entraîner la désactivation en douceur d'un complément VSTO, si ce dernier lève une exception non gérée pendant l'exécution du gestionnaire d'événements <xref:Microsoft.Office.Tools.AddIn.Startup> .  
  
> [!NOTE]  
>  Quand vous réactivez un complément VSTO désactivé en douceur, l'application essaie immédiatement de charger le complément VSTO. Si le problème qui a obligé initialement l'application à désactiver en douceur le complément VSTO n'a pas été résolu, l'application désactivera à nouveau en douceur le complément VSTO.  
  
#### <a name="to-re-enable-an-vsto-add-in"></a>Pour réactiver un complément VSTO  
  
1.  Dans l'application, cliquez sur l'onglet **Fichier** .  
  
2.  Cliquez sur le bouton *Options de* **nom_application** .  
  
3.  Dans le volet des catégories, cliquez sur **Compléments**.  
  
4.  Dans le volet d'informations, vérifiez que le complément VSTO apparaît dans la liste **Compléments d'applications inactifs** .  
  
     La colonne **Nom** indique le nom de l'assembly, et la colonne **Emplacement** indique le chemin d'accès complet du manifeste de l'application.  
  
5.  Dans la zone **Gérer** , cliquez sur **Compléments COM**, puis sur **Atteindre**.  
  
6.  Dans la boîte de dialogue **Compléments COM** , cochez la case en regard du complément VSTO désactivé.  
  
7.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération de Solutions Office](../vsto/building-office-solutions.md)   
 [Débogage de projets Office](../vsto/debugging-office-projects.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)  
  
  