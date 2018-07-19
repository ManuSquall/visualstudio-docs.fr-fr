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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 93d39aedc04cbdaebc35c892a8393ca394f44898
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36281064"
---
# <a name="configure-service-reference-dialog-box"></a>Configurer la référence de service (boîte de dialogue)

Le **configurer la référence de Service** boîte de dialogue vous permet de configurer le comportement des services Windows Communication Foundation (WCF).

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Pour accéder à la **configurer la référence de Service** boîte de dialogue, avec le bouton droit, un service de référence dans **l’Explorateur de solutions** et choisissez **configurer la référence de Service**. Vous pouvez également accéder à la boîte de dialogue en cliquant sur le **avancé** situé dans le **ajouter une référence de Service, boîte de dialogue**.

## <a name="task-list"></a>Liste des tâches

- Pour modifier l’adresse où un service WCF est hébergé, entrez la nouvelle adresse dans le **adresse** champ.

- Pour modifier le niveau d’accès pour les classes dans un client WCF, sélectionnez un mot clé de niveau d’accès dans le **niveau pour les classes générées d’accès** liste.

- Pour appeler les méthodes d’un service WCF de façon asynchrone, sélectionnez le **générer des opérations asynchrones** case à cocher.

- Pour générer des types de contrat de message dans un client WCF, sélectionnez le **toujours générer des contrats de message** case à cocher.

- Pour spécifier les types de collections de dictionnaires ou de listes pour un client WCF, sélectionnez les types à partir de la **type de Collection** et **type de collection dictionnaire** répertorie.

- Pour désactiver le partage de type, désactivez le **réutiliser les types dans les assemblys référencés** case à cocher. Pour activer le partage de type d’un sous-ensemble d’assemblys référencés, sélectionnez le **réutiliser les types dans les assemblys référencés** case à cocher, sélectionnez **réutiliser les types dans les assemblys référencés spécifiés**, puis sélectionnez le texte souhaité fait référence dans le **liste des assemblys référencés**.

## <a name="uielement-list"></a>Liste UIElement

 **Adresse**

 Met à jour l’adresse Web dans lesquels une référence de service recherche pour un service. Par exemple, pendant le développement, le service peut être hébergé sur un serveur de développement et transféré ultérieurement vers un serveur de production, ce qui nécessite un changement d’adresse.

> [!NOTE]
> L’élément adresse n’est pas disponible lorsque le **configurer la référence de Service** boîte de dialogue s’affiche à partir de la **ajouter une référence de Service, boîte de dialogue**.

 **Niveau d’accès pour les classes générées**

 Détermine le niveau d'accès du code pour les classes clientes WCF.

> [!NOTE]
> Pour les projets de site web, cette option a toujours la valeur `Public` et ne peut pas être modifiée. Pour plus d’informations, consultez [dépannage de références de service](../data-tools/troubleshooting-service-references.md).

 **Générer des opérations asynchrones**

 Détermine si les méthodes de service WCF est appelée de façon synchrone (valeur par défaut) ou asynchrone.

 **Générer des opérations basées sur des tâches**

 Lorsque vous écrivez du code asynchrone, cette option vous permet de tirer parti de la bibliothèque (parallèle de tâches) qui a été introduit avec .NET 4. Consultez [(TPL) de bibliothèque parallèle de tâches](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Toujours générer des contrats de message**

 Détermine si les types de contrat de message sont générés pour un client WCF. Pour plus d’informations sur les contrats de message, consultez [à l’aide de contrats de message](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Type de collection**

 Spécifie le type de collection de listes pour un client WCF. Le type par défaut est <xref:System.Array>.

 **Type de collection dictionnaire**

 Spécifie le type de collection de dictionnaires pour un client WCF. Le type par défaut est <xref:System.Collections.Generic.Dictionary%602>.

 **Réutiliser les types dans les assemblys référencés**

 Détermine si un client WCF essaie de réutiliser ce qui existe déjà dans les assemblys référencés au lieu de générer de nouveaux types lorsqu’un service est ajouté ou mis à jour. Cette option est cochée par défaut.

 **Réutiliser les types dans tous les assemblys référencés**

 Lorsque sélectionné, tous les types dans les **liste des assemblys référencés** sont réutilisés si possible. Cette option est activée par défaut.

 **Réutiliser les types dans les assemblys référencés spécifiés**

 Lorsque sélectionné, seuls les types sélectionnés dans le **liste des assemblys référencés** sont réutilisées.

 **Liste des assemblys référencés**

 Contient la liste des assemblys référencés pour le projet ou le site web. Lorsque vous sélectionnez **réutiliser les types dans les assemblys référencés spécifiés**, vous pouvez sélectionner ou effacer des assemblys individuels.

 **Ajouter une référence Web**

 Affiche le **ajouter une référence Web** boîte de dialogue.

> [!NOTE]
> Cette option doit uniquement être utilisée pour les projets qui ciblent la version 2.0 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

> [!NOTE]
> Le **ajouter une référence Web** bouton est disponible uniquement lorsque le **configurer la référence de Service** boîte de dialogue s’affiche à partir de la **ajouter une référence de Service, boîte de dialogue**.

## <a name="see-also"></a>Voir aussi

- [Comment : ajouter une référence à un service web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Services Windows Communication Foundation et WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)