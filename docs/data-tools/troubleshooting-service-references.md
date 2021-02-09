---
title: Dépannage des références de service
description: Passez en revue les problèmes courants qui peuvent se produire lorsque vous utilisez des références Windows Communication Foundation (WCF) ou Services de données WCF dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 909291e3f9762593a58df93a9ccc7fe2e82b7952
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866357"
---
# <a name="troubleshoot-service-references"></a>Dépanner les références de service

Cette rubrique répertorie les problèmes courants qui peuvent se produire lorsque vous utilisez des références Windows Communication Foundation (WCF) ou Services de données WCF dans Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Erreur lors du retour de données à partir d’un service

Lorsque vous retournez un `DataSet` ou `DataTable` à partir d’un service, vous pouvez recevoir l’exception « le quota de taille maximale pour les messages entrants a été dépassé ». Par défaut, la `MaxReceivedMessageSize` propriété de certaines liaisons est définie sur une valeur relativement faible pour limiter l’exposition aux attaques par déni de service. Vous pouvez augmenter cette valeur pour empêcher l’exception. Pour plus d’informations, consultez <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Pour résoudre ce problème :

1. Dans **Explorateur de solutions**, double-cliquez sur le fichier *app.config* pour l’ouvrir.

2. Recherchez la `MaxReceivedMessageSize` propriété et affectez-lui une valeur plus grande.

## <a name="cannot-find-a-service-in-my-solution"></a>Impossible de trouver un service dans ma solution

Lorsque vous cliquez sur le bouton **découvrir** dans la boîte de dialogue **Ajouter des références de service** , un ou plusieurs projets de bibliothèque de services WCF dans la solution n’apparaissent pas dans la liste des services. Cela peut se produire si une bibliothèque de services a été ajoutée à la solution mais n’a pas encore été compilée.

Pour résoudre ce problème :

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet Bibliothèque du service WCF, puis cliquez sur **générer**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Erreur lors de l’accès à un service sur un bureau à distance

Lorsqu’un utilisateur accède à un service WCF hébergé sur le Web via une connexion Bureau à distance et que l’utilisateur ne dispose pas d’autorisations d’administration, l’authentification NTLM est utilisée. Si l’utilisateur ne dispose pas d’autorisations d’administration, l’utilisateur peut recevoir le message d’erreur suivant : « la requête HTTP n’est pas autorisée avec le schéma d’authentification client «Anonymous ». L’en-tête d’authentification reçu du serveur était « NTLM ».

Pour résoudre ce problème :

1. Dans le projet de site Web, ouvrez les pages de **Propriétés** .

2. Sous l’onglet **options de démarrage** , désactivez la case à cocher **authentification NTLM** .

    > [!NOTE]
    > Vous devez désactiver l’authentification NTLM uniquement pour les sites Web qui contiennent exclusivement des services WCF. La sécurité pour les services WCF est gérée à l’aide de la configuration dans le fichier *web.config* . L’authentification NTLM n’est donc pas nécessaire.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Le paramètre niveau d’accès pour les classes générées n’a aucun effet

La définition de l’option **niveau d’accès pour les classes générées** de la boîte de dialogue **configurer les références de service** sur **interne** ou **Friend** peut ne pas toujours fonctionner. Même si l’option semble être définie dans la boîte de dialogue, les classes de prise en charge résultantes sont générées avec un niveau d’accès de `Public` .

Il s’agit d’une limitation connue de certains types, tels que ceux sérialisés à l’aide du <xref:System.Xml.Serialization.XmlSerializer> .

## <a name="error-debugging-service-code"></a>Erreur lors du débogage du code du service

Quand vous exécutez un pas à pas détaillé dans le code d’un service WCF à partir du code client, vous pouvez recevoir une erreur liée à des symboles manquants. Cela peut se produire lorsqu’un service qui faisait partie de votre solution a été déplacé ou supprimé de la solution.

Lorsque vous ajoutez pour la première fois une référence à un service WCF qui fait partie de la solution actuelle, une dépendance de génération explicite est ajoutée entre le projet de service et le projet de client de service. Cela garantit que le client accède toujours aux fichiers binaires de service à jour, ce qui est particulièrement important pour les scénarios de débogage tels que l’exécution pas à pas du code client dans le code de service.

Si le projet de service est supprimé de la solution, cette dépendance de génération explicite est invalidée. Visual Studio ne peut plus garantir que le projet de service est régénéré si nécessaire.

Pour corriger cette erreur, vous devez reconstruire manuellement le projet de service :

1. Dans le menu **Outils** , cliquez sur **Options**.

2. Dans la boîte de dialogue **options** , développez **projets et solutions**, puis sélectionnez **général**.

3. Assurez-vous que la case à cocher **afficher les configurations de build avancées** est activée, puis cliquez sur **OK**.

4. Chargez le projet de service WCF.

5. Dans la boîte de dialogue **Configuration Manager** , définissez la configuration de la **solution active** à **Déboguer**. Pour plus d’informations, consultez [Guide pratique pour créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).

6. Dans **Explorateur de solutions**, sélectionnez le projet de service WCF.

7. Dans le menu **générer** , cliquez sur **régénérer** pour régénérer le projet de service WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>Services de données WCF ne pas afficher dans le navigateur

Lorsqu’il tente d’afficher une représentation XML de données dans un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] , Internet Explorer peut interpréter les données comme un flux RSS. Assurez-vous que l’option permettant d’afficher les flux RSS est désactivée.

Pour corriger cette erreur, désactivez les flux RSS :

1. Dans Internet Explorer, dans le menu **Outils**, cliquez sur **Options Internet**.

2. Sous l’onglet **contenu** , dans la section **flux** , cliquez sur **paramètres**.

3. Dans la boîte de dialogue **paramètres de flux** , désactivez la case à cocher **activer le mode lecture du flux** , puis cliquez sur **OK**.

4. Cliquez sur **OK** pour fermer la boîte de dialogue **Options Internet** .

## <a name="see-also"></a>Voir aussi

- [Services Windows Communication Foundation et services de données WCF dans Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
