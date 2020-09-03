---
title: Configurer la référence de service, boîte de dialogue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac8f4cf619bbdd007bb7aa570f549ae3c0b50e86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651116"
---
# <a name="configure-service-reference-dialog-box"></a>Configurer la référence de service (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La boîte de dialogue **configurer la référence de service** vous permet de configurer le comportement des [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] services.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Pour accéder à la boîte de dialogue **Configurer la référence de service**, cliquez avec le bouton droit sur une référence de service dans l’**Explorateur de solutions** et choisissez **Configurer la référence de service**. Vous pouvez également accéder à la boîte de dialogue en cliquant sur le bouton **Avancé** dans la **boîte de dialogue Ajouter une référence de service**.

## <a name="task-list"></a>Liste des tâches

- Pour modifier l’adresse d’hébergement d’un service WCF, entrez la nouvelle adresse dans le champ **Adresse**.

- Pour modifier le niveau d’accès des classes dans un client WCF, sélectionnez un mot clé de niveau d’accès dans la liste **Niveau d’accès pour les classes générées**.

- Pour appeler de façon asynchrone les méthodes d’un service WCF, cochez la case **Générer des opérations asynchrones**.

- Pour générer des types de contrats de message dans un client WCF, cochez la case **Toujours générer des contrats de message**.

- Pour spécifier des types de collections de dictionnaires ou de listes pour un client WCF, sélectionnez les types dans les listes **Type de collection** et **Type de collection Dictionnaire**.

- Pour désactiver le partage de type, décochez la case **Réutiliser les types dans les assemblys référencés**. Pour activer le partage de type d’un sous-ensemble d’assemblys référencés, cochez la case **Réutiliser les types dans les assemblys référencés**, sélectionnez **Réutiliser les types dans les assemblys référencés spécifiés**, puis sélectionnez les références souhaitées dans la **Liste des assemblys référencés**.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 **Adresse** Utilisé pour mettre à jour l’adresse Web à laquelle une référence de service recherche un service. Par exemple, pendant le développement, le service peut être hébergé sur un serveur de développement, puis transféré ultérieurement vers un serveur de production, ce qui nécessite un changement d'adresse.

> [!NOTE]
> L’élément Adresse n’est pas disponible quand la boîte de dialogue **Configurer la référence de service** est affichée à partir de la boîte de dialogue **Ajouter une référence de service**.

 **Niveau d’accès pour les classes générées** Détermine le niveau d’accès du code pour les classes clientes WCF.

> [!NOTE]
> Pour les projets de site web, cette option a toujours la valeur `Public` et ne peut pas être modifiée. Pour plus d’informations, consultez [Dépannage des références de service](../data-tools/troubleshooting-service-references.md).

 **Générer des opérations asynchrones** Détermine si les méthodes de service WCF sont appelées de façon synchrone (valeur par défaut) ou asynchrone.

 **Générer des opérations basées sur les tâches** Lors de l’écriture de code asynchrone, cette option vous permet de tirer parti de la bibliothèque parallèle de tâches (TPL) qui a été introduite avec .net 4. Consultez [bibliothèque parallèle de tâches (TPL)](https://msdn.microsoft.com/library/dd460717.aspx).

 **Toujours générer des contrats de message** Détermine si les types de contrat de message sont générés pour un client WCF. Pour plus d’informations sur les contrats de message, consultez [utilisation de contrats de message](https://msdn.microsoft.com/library/1e19c64a-ae84-4c2f-9155-91c54a77c249).

 **Type de collection** Spécifie le type de collection de listes pour un client WCF. Le type par défaut est <xref:System.Array>.

 **Type de collection dictionary** Spécifie le type de collection dictionnaire pour un client WCF. Le type par défaut est <xref:System.Collections.Generic.Dictionary%602>.

 **Réutiliser les types dans les assemblys référencés** Détermine si un client WCF essaie de réutiliser qui existe déjà dans les assemblys référencés au lieu de générer de nouveaux types lorsqu’un service est ajouté ou mis à jour. Cette option est cochée par défaut.

 **Réutiliser les types dans tous les assemblys référencés** Lorsque cette option est sélectionnée, tous les types dans la **liste des assemblys référencés** sont réutilisés si possible. Cette option est activée par défaut.

 **Réutiliser les types dans les assemblys référencés spécifiés** Lorsque cette option est sélectionnée, seuls les types sélectionnés dans la **liste des assemblys référencés** sont réutilisés.

 **Liste des assemblys référencés** Contient une liste d’assemblys référencés pour le projet ou le site Web. Lorsque **l’option réutiliser les types dans les assemblys référencés spécifiés** est sélectionnée, les assemblys individuels peuvent être sélectionnés ou effacés.

 **Ajouter une référence Web** Affiche la [boîte de dialogue plume : ajouter une référence Web](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).

> [!NOTE]
> Cette option doit uniquement être utilisée pour les projets qui ciblent la version 2.0 du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

> [!NOTE]
> Le bouton **Ajouter une référence Web** est disponible uniquement lorsque la boîte de dialogue **configurer la référence de service** s’affiche dans la boîte de **dialogue Ajouter une référence de service**.

## <a name="see-also"></a>Voir aussi
 [Comment : ajouter, mettre à jour ou supprimer une référence de service](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9) [Comment : ajouter une référence à un service Web](https://msdn.microsoft.com/library/952e49a1-567e-4a74-8cd7-f2e7b62c3168) [Windows Communication Foundation services et WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)
