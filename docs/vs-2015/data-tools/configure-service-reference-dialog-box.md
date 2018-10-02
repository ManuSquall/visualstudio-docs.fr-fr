---
title: Configurer la boîte de dialogue de référence de Service | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 60a1c7a057495b89aa8923d424fb09d9ecb1c232
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495959"
---
# <a name="configure-service-reference-dialog-box"></a>Configurer la référence de service (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [configurer une référence de Service, boîte de dialogue](https://docs.microsoft.com/visualstudio/data-tools/configure-service-reference-dialog-box).  
  
  
Le **configurer la référence de Service** boîte de dialogue vous permet de configurer le comportement de [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] services.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Pour accéder à la **configurer la référence de Service** boîte de dialogue, avec le bouton droit, un service de référence dans **l’Explorateur de solutions** et choisissez **configurer la référence de Service**. Vous pouvez également accéder à la boîte de dialogue en cliquant sur le **avancé** situé dans le **ajouter une référence de Service, boîte de dialogue**.  
  
## <a name="task-list"></a>Liste des tâches  
  
-   Pour modifier l’adresse où un service WCF est hébergé, entrez la nouvelle adresse dans le **adresse** champ.  
  
-   Pour modifier le niveau d’accès pour les classes dans un client WCF, sélectionnez un mot clé de niveau d’accès dans le **niveau pour les classes générées d’accès** liste.  
  
-   Pour appeler les méthodes d’un service WCF de façon asynchrone, sélectionnez le **générer des opérations asynchrones** case à cocher.  
  
-   Pour générer des types de contrat de message dans un client WCF, sélectionnez le **toujours générer des contrats de message** case à cocher.  
  
-   Pour spécifier les types de collections de dictionnaires ou de listes pour un client WCF, sélectionnez les types à partir de la **type de Collection** et **type de collection dictionnaire** répertorie.  
  
-   Pour désactiver le partage de type, désactivez le **réutiliser les types dans les assemblys référencés** case à cocher. Pour activer le partage de type d’un sous-ensemble d’assemblys référencés, sélectionnez le **réutiliser les types dans les assemblys référencés** case à cocher, sélectionnez **réutiliser les types dans les assemblys référencés spécifiés**, puis sélectionnez le texte souhaité fait référence dans le **liste des assemblys référencés**.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Adresse**  
 Permet de mettre à jour l'adresse web qu'une référence de service utilise pour rechercher un service. Par exemple, pendant le développement, le service peut être hébergé sur un serveur de développement, puis transféré ultérieurement vers un serveur de production, ce qui nécessite un changement d'adresse.  
  
> [!NOTE]
>  L’élément adresse n’est pas disponible lorsque le **configurer la référence de Service** boîte de dialogue s’affiche à partir de la **ajouter une référence de Service, boîte de dialogue**.  
  
 **Niveau d’accès pour les classes générées**  
 Détermine le niveau d'accès du code pour les classes clientes WCF.  
  
> [!NOTE]
>  Pour les projets de site web, cette option a toujours la valeur `Public` et ne peut pas être modifiée. Pour plus d’informations, consultez [dépannage de références de Service](../data-tools/troubleshooting-service-references.md).  
  
 **Générer des opérations asynchrones**  
 Détermine si les méthodes de service WCF sont appelées de façon synchrone (valeur par défaut) ou de façon asynchrone.  
  
 **Générer des opérations basées sur des tâches**  
 Dans le cadre de l’écriture de code asynchrone, cette option vous permet d’exploiter la bibliothèque parallèle de tâches (TPL) introduite dans .Net 4. Consultez [(TPL) de bibliothèque parallèle de tâches](http://msdn.microsoft.com/library/dd460717.aspx).  
  
 **Toujours générer des contrats de message**  
 Détermine si des types de contrats de message sont générés pour un client WCF. Pour plus d’informations sur les contrats de message, consultez [Using Message Contracts](http://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).  
  
 **Type de collection**  
 Spécifie le type de collection de listes pour un client WCF. Le type par défaut est <xref:System.Array>.  
  
 **Type de collection dictionnaire**  
 Spécifie le type de collection de dictionnaires pour un client WCF. Le type par défaut est <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Réutiliser les types dans les assemblys référencés**  
 Détermine si un client WCF essaie de réutiliser ce qui existe déjà dans les assemblys référencés au lieu de générer de nouveaux types quand un service est ajouté ou mis à jour. Cette option est cochée par défaut.  
  
 **Réutiliser les types dans tous les assemblys référencés**  
 Lorsque sélectionné, tous les types dans les **liste des assemblys référencés** seront réutilisés si possible. Cette option est activée par défaut.  
  
 **Réutiliser les types dans les assemblys référencés spécifiés**  
 Lorsque sélectionné, seuls les types sélectionnés dans le **liste des assemblys référencés** sera réutilisé.  
  
 **Liste des assemblys référencés**  
 Contient la liste des assemblys référencés pour le projet ou le site web. Lorsque **réutiliser les types dans les assemblys référencés spécifiés** est sélectionnée, des assemblys individuels peuvent être activées ou désactivées.  
  
 **Ajouter une référence Web**  
 Affiche le [NIB : ajouter la référence Web, boîte de dialogue](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Cette option doit uniquement être utilisée pour les projets qui ciblent la version 2.0 du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  Le **ajouter une référence Web** bouton est disponible uniquement lorsque le **configurer la référence de Service** boîte de dialogue s’affiche à partir de la **ajouter une référence de Service, boîte de dialogue**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ajouter, mettre à jour ou supprimer une référence de Service](http://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)   
 [Comment : ajouter une référence à un Service Web](http://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168)   
 [Services Windows Communication Foundation et WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)

