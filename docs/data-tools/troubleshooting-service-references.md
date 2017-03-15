---
title: "Troubleshooting Service References | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther"
  - "msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo"
  - "msvse_wcf.Err.ErrorOnOK"
  - "msvse_wcf.cfg.ConfigurationErrorsException"
helpviewer_keywords: 
  - "service references [Visual Studio], troubleshooting"
  - "WCF services, troubleshooting"
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Troubleshooting Service References
Cette rubrique répertorie les problèmes courants susceptibles de se produire lorsque vous utilisez des références [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] ou [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Erreur lors du retour de données d'un service  
 Lorsque vous retournez un `DataSet` ou une `DataTable` d'un service, vous recevrez peut\-être une exception de type « La taille maximum du quota pour les messages entrants a été excédée ».  Par défaut, la propriété `MaxReceivedMessageSize` pour certaines liaisons est définie selon une valeur relativement faible afin de limiter les risques d'exposition à des attaques par déni de service.  Vous pouvez augmenter cette valeur pour éviter l'exception.  Pour plus d'informations, consultez <xref:System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize%2A>.  
  
 Pour corriger cette erreur :  
  
1.  Dans l'**Explorateur de solutions**, double\-cliquez sur le fichier app.config pour l'ouvrir.  
  
2.  Recherchez la propriété `MaxReceivedMessageSize` et affectez\-lui une valeur plus importante.  
  
## Impossible de trouver un service dans Ma solution.  
 Lorsque vous cliquez sur le bouton **Découvrir** dans la boîte de dialogue **Ajouter des références de services**, un ou plusieurs projets Bibliothèque de services WCF dans la solution n'apparaissent pas dans la liste des services.  Cela peut se produire si une bibliothèque de services a été ajoutée à la solution, mais n'a pas encore été compilée.  
  
 Pour corriger cette erreur :  
  
-   Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet Bibliothèque de services WCF, puis cliquez sur **Générer**.  
  
## Erreur lors de l'accès à un service sur un Bureau à distance  
 Lorsqu'un utilisateur accède à un service WCF hébergé sur le Web sur une connexion Bureau à distance sans autorisation administrative, l'authentification NTLM est alors utilisée.  Si l'utilisateur ne dispose pas d'autorisations administratives, il peut recevoir le message d'erreur suivant : « La requête HTTP n'est pas autorisée avec le schéma d'authentification client 'Anonyme'.  L'en\-tête d'authentification reçu du serveur était 'NTLM'. ».  
  
 Pour corriger cette erreur :  
  
1.  Dans le projet de site Web, ouvrez les pages **Propriétés**.  
  
2.  Sous l'onglet **Options de démarrage**, désactivez la case à cocher **Authentification NTLM**.  
  
    > [!NOTE]
    >  Vous ne devez désactiver l'authentification NTLM que pour les sites Web qui contiennent exclusivement des services WCF.  La gestion de la sécurité des services WCF s'effectue via le fichier de configuration Web.config.  L'authentification NTLM n'est de ce fait pas nécessaire.  
  
 Pour plus d'informations, consultez [Dépannage des exceptions : System.ServiceModel.Security.MessageSecurityException](../misc/troubleshooting-exceptions-system-servicemodel-security-messagesecurityexception.md).  
  
## Le niveau d'accès pour le paramètre Classes générées est sans effet.  
 Définir l'option **Niveau d'accès pour les classes générées** dans la boîte de dialogue **Configurer les références de service** sur **Interne** ou **Friend** peut ne pas fonctionner dans tous les cas.  Bien que l'option semble être définie dans la boîte de dialogue, les classes de prise en charge qui en résultent seront générées avec un niveau d'accès `Public`.  
  
 C'est une limitation connue de certains types, tels que ceux qui sont sérialisés à l'aide du <xref:System.Xml.Serialization.XmlSerializer>.  
  
## Erreur lors du débogage du code de service  
 Lorsque vous exécutez pas à pas le code d'un service WCF à partir du code client, vous pouvez recevoir une erreur concernant des symboles manquants.  Cela peut se produire lorsqu'un service qui faisait partie de votre solution a été déplacé ou supprimé de celle\-ci.  
  
 Lorsque vous ajoutez pour la première fois une référence à un service WCF qui fait partie de la solution actuelle, une dépendance de génération explicite est ajoutée entre le projet de service et le projet de client de service.  Le client est ainsi assuré d'accéder en permanence à des binaires de service à jour, ce qui est particulièrement important pour déboguer des scénarios tels que l'exécution pas à pas du code client dans le code de service.  
  
 Si le projet de service est supprimé de la solution, cette dépendance de génération explicite est invalidée.  Visual Studio ne peut plus garantir la régénération du projet de service selon les besoins.  
  
 Pour résoudre cette erreur, vous devez régénérer le projet de service manuellement :  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis sélectionnez **Général**.  
  
3.  Assurez\-vous que la case à cocher **Afficher les configurations de build avancées** est activée, puis cliquez sur **OK**.  
  
4.  Chargez le projet de service WCF.  Pour plus d'informations, consultez [Comment : créer des solutions à plusieurs projets](http://msdn.microsoft.com/fr-fr/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).  
  
5.  Dans la boîte de dialogue **Gestionnaire de configurations**, définissez **Configuration de la solution active** sur **Débogage**.  Pour plus d'informations, consultez [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md).  
  
6.  Dans l'**Explorateur de solutions**, sélectionnez le projet de service WCF.  
  
7.  Dans le menu **Générer**, cliquez sur **Régénérer** pour régénérer le projet de service WCF.  
  
## Les services de données WCF ne s'affichent pas dans le navigateur  
 Lorsque Microsoft Internet Explorer tente d'afficher une représentation XML des données dans un [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], les données peuvent être interprétées de façon incorrecte comme un flux RSS.  Vous devez vous assurer que l'option permettant d'afficher les flux RSS est désactivée.  
  
 Pour corriger cette erreur, désactivez les flux RSS :  
  
1.  Dans Internet Explorer, dans le menu **Outils**, cliquez sur **Options Internet**.  
  
2.  Sous l'onglet **Contenu**, dans la section **Flux**, cliquez sur **Paramètres**.  
  
3.  Dans la boîte de dialogue **Paramètres de flux**, désactivez la case à cocher **Activer le mode Lecture du flux**, puis cliquez sur **OK**.  
  
4.  Cliquez sur **OK** pour fermer la boîte de dialogue **Options Internet**.  
  
## Voir aussi  
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Consuming ASMX and WCF Services Sample](http://msdn.microsoft.com/fr-fr/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)