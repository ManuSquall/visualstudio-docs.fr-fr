---
title: Configurer la référence de service (boîte de dialogue)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b622fc77884acde5b81d886628afce9f077e86a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567971"
---
# <a name="configure-service-reference-dialog-box"></a>Configurer la référence de service (boîte de dialogue)

Le **configurer la référence de Service** boîte de dialogue vous permet de configurer le comportement des services Windows Communication Foundation (WCF).

Pour accéder à la boîte de dialogue **Configurer la référence de service**, cliquez avec le bouton droit sur une référence de service dans l’**Explorateur de solutions** et choisissez **Configurer la référence de service**. Vous pouvez également accéder à la boîte de dialogue en cliquant sur le bouton **Avancé** dans la **boîte de dialogue Ajouter une référence de service**.

## <a name="task-list"></a>Liste des tâches

- Pour modifier l’adresse d’hébergement d’un service WCF, entrez la nouvelle adresse dans le champ **Adresse**.

- Pour modifier le niveau d’accès des classes dans un client WCF, sélectionnez un mot clé de niveau d’accès dans la liste **Niveau d’accès pour les classes générées**.

- Pour appeler de façon asynchrone les méthodes d’un service WCF, cochez la case **Générer des opérations asynchrones**.

- Pour générer des types de contrats de message dans un client WCF, cochez la case **Toujours générer des contrats de message**.

- Pour spécifier des types de collections de dictionnaires ou de listes pour un client WCF, sélectionnez les types dans les listes **Type de collection** et **Type de collection Dictionnaire**.

- Pour désactiver le partage de type, décochez la case **Réutiliser les types dans les assemblys référencés**. Pour activer le partage de type d’un sous-ensemble d’assemblys référencés, cochez la case **Réutiliser les types dans les assemblys référencés**, sélectionnez **Réutiliser les types dans les assemblys référencés spécifiés**, puis sélectionnez les références souhaitées dans la **Liste des assemblys référencés**.

## <a name="uielement-list"></a>Liste UIElement

 **Adresse**

 Met à jour l’adresse web dans lesquels une référence de service recherche pour un service. Par exemple, pendant le développement, le service peut être hébergé sur un serveur de développement et transféré ultérieurement vers un serveur de production, ce qui nécessite un changement d’adresse.

> [!NOTE]
> L’élément Adresse n’est pas disponible quand la boîte de dialogue **Configurer la référence de service** est affichée à partir de la boîte de dialogue **Ajouter une référence de service**.

 **Niveau d’accès pour les classes générées**

 Détermine le niveau d'accès du code pour les classes clientes WCF.

> [!NOTE]
> Pour les projets de site web, cette option a toujours la valeur `Public` et ne peut pas être modifiée. Pour plus d’informations, consultez [Dépannage des références de service](../data-tools/troubleshooting-service-references.md).

 **Générer des opérations asynchrones**

 Détermine si les méthodes de service WCF est appelée de façon synchrone (valeur par défaut) ou asynchrone.

 **Générer des opérations basées sur les tâches**

 Lorsque vous écrivez du code asynchrone, cette option vous permet de tirer parti de la bibliothèque (parallèle de tâches) qui a été introduit avec .NET 4. Consultez [(TPL) de bibliothèque parallèle de tâches](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Toujours générer des contrats de message**

 Détermine si les types de contrat de message sont générés pour un client WCF. Pour plus d’informations sur les contrats de message, consultez [Utilisation de contrats de message](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Type de collection**

 Spécifie le type de collection de listes pour un client WCF. Le type par défaut est <xref:System.Array>.

 **Type de collection Dictionnaire**

 Spécifie le type de collection de dictionnaires pour un client WCF. Le type par défaut est <xref:System.Collections.Generic.Dictionary%602>.

 **Réutiliser les types dans les assemblys référencés**

 Détermine si un client WCF essaie de réutiliser ce qui existe déjà dans les assemblys référencés au lieu de générer de nouveaux types lorsqu’un service est ajouté ou mis à jour. Cette option est cochée par défaut.

 **Réutiliser les types dans tous les assemblys référencés**

 Lorsque sélectionné, tous les types dans les **liste des assemblys référencés** sont réutilisés si possible. Cette option est activée par défaut.

 **Réutiliser les types dans les assemblys référencés spécifiés**

 Lorsque sélectionné, seuls les types sélectionnés dans le **liste des assemblys référencés** sont réutilisées.

 **Liste des assemblys référencés**

 Contient une liste d’assemblys référencés pour le projet ou le site Web. Lorsque vous sélectionnez **réutiliser les types dans les assemblys référencés spécifiés**, vous pouvez sélectionner ou effacer des assemblys individuels.

 **Ajouter une référence web**

 Affiche la boîte de dialogue **Ajouter une référence web**.

> [!NOTE]
> Cette option doit uniquement être utilisée pour les projets qui ciblent la version 2.0 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].
>
> [!NOTE]
> Le **ajouter une référence Web** bouton est disponible uniquement lorsque le **configurer la référence de Service** boîte de dialogue s’affiche à partir de la **ajouter une référence de Service, boîte de dialogue**.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Ajoutez une référence à un service web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Services Windows Communication Foundation et WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)