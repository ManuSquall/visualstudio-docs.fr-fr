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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 033663c347a39c63a76bddd10625bdc86cec1f00
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72642857"
---
# <a name="configure-service-reference-dialog-box"></a>Configurer la référence de service (boîte de dialogue)

La boîte de dialogue **configurer la référence de service** vous permet de configurer le comportement des services Windows Communication Foundation (WCF).

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

Met à jour l’adresse Web à laquelle une référence de service recherche un service. Par exemple, lors du développement, le service peut être hébergé sur un serveur de développement, puis déplacé ultérieurement vers un serveur de production, ce qui nécessite un changement d’adresse.

> [!NOTE]
> L’élément Adresse n’est pas disponible quand la boîte de dialogue **Configurer la référence de service** est affichée à partir de la boîte de dialogue **Ajouter une référence de service**.

**Niveau d’accès pour les classes générées**

Détermine le niveau d'accès du code pour les classes clientes WCF.

> [!NOTE]
> Pour les projets de site web, cette option a toujours la valeur `Public` et ne peut pas être modifiée. Pour plus d’informations, consultez [Dépannage des références de service](../data-tools/troubleshooting-service-references.md).

**Générer des opérations asynchrones**

Détermine si les méthodes de service WCF sont appelées de façon synchrone (valeur par défaut) ou asynchrone.

**Générer des opérations basées sur les tâches**

Lors de l’écriture de code asynchrone, cette option vous permet de tirer parti de la bibliothèque parallèle de tâches (TPL) qui a été introduite avec .NET 4. Consultez [bibliothèque parallèle de tâches (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

**Toujours générer des contrats de message**

Détermine si les types de contrat de message sont générés pour un client WCF. Pour plus d’informations sur les contrats de message, consultez [Utilisation de contrats de message](/dotnet/framework/wcf/feature-details/using-message-contracts).

**Type de collection**

Spécifie le type de collection de listes pour un client WCF. Le type par défaut est <xref:System.Array>.

**Type de collection Dictionnaire**

Spécifie le type de collection de dictionnaires pour un client WCF. Le type par défaut est <xref:System.Collections.Generic.Dictionary%602>.

**Réutiliser les types dans les assemblys référencés**

Détermine si un client WCF tente de réutiliser ce qui existe déjà dans les assemblys référencés au lieu de générer de nouveaux types lorsqu’un service est ajouté ou mis à jour. Cette option est cochée par défaut.

**Réutiliser les types dans tous les assemblys référencés**

Lorsque cette option est sélectionnée, tous les types dans la **liste des assemblys référencés** sont réutilisés si possible. Cette option est activée par défaut.

**Réutiliser les types dans les assemblys référencés spécifiés**

Lorsque cette option est sélectionnée, seuls les types sélectionnés dans la **liste des assemblys référencés** sont réutilisés.

**Liste des assemblys référencés**

Contient une liste d’assemblys référencés pour le projet ou le site Web. Lorsque vous sélectionnez **réutiliser les types dans les assemblys référencés spécifiés**, vous pouvez sélectionner ou effacer des assemblys individuels.

**Ajouter une référence web**

Affiche la boîte de dialogue **Ajouter une référence web**.

> [!NOTE]
> Cette option doit être utilisée uniquement pour les projets qui ciblent la version 2,0 du .NET Framework.
>
> [!NOTE]
> Le bouton **Ajouter une référence Web** est disponible uniquement lorsque la boîte de dialogue **configurer la référence de service** s’affiche dans la boîte de **dialogue Ajouter une référence de service**.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour ajouter une référence à un service web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Services Windows Communication Foundation et WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)