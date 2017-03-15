---
title: "Configurer la r&#233;f&#233;rence de service, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.dlg.ConfigureServiceReference"
helpviewer_keywords: 
  - "Services WCF, boîte de dialogue Configurer la référence de service"
  - "références de service (Visual Studio), configuration du comportement"
  - "Configurer la référence de service (boîte de dialogue)"
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: 16
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Configurer la r&#233;f&#233;rence de service, bo&#238;te de dialogue
La boîte de dialogue **Configurer la référence de service** vous permet de configurer le comportement des services [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)].  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Pour accéder à la boîte de dialogue **Configurer la référence de service**, cliquez avec le bouton droit sur une référence de service dans l'**Explorateur de solutions** et choisissez **Configurer la référence de service**.  Vous pouvez également accéder à la boîte de dialogue en cliquant sur le bouton **Avancé** dans la [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md).  
  
## Liste des tâches  
  
-   Pour modifier l'adresse d'hébergement d'un service WCF, entrez la nouvelle adresse dans le champ **Adresse**.  
  
-   Pour modifier le niveau d'accès des classes dans un client WCF, sélectionnez un mot clé de niveau d'accès dans la liste **Niveau d'accès pour les classes générées**.  
  
-   Pour appeler de façon asynchrone les méthodes d'un service WCF, cochez la case **Générer des opérations asynchrones**.  
  
-   Pour générer des types de contrats de message dans un client WCF, cochez la case **Toujours générer des contrats de message**.  
  
-   Pour spécifier des types de collections de dictionnaires ou de listes pour un client WCF, sélectionnez les types dans les listes **Type de collection** et **Type de collection Dictionnaire**.  
  
-   Pour désactiver le partage de type, décochez la case **Réutiliser les types dans les assemblys référencés**.  Pour activer le partage de type d'un sous\-ensemble d'assemblys référencés, cochez la case **Réutiliser les types dans les assemblys référencés**, sélectionnez **Réutiliser les types dans les assemblys référencés spécifiés** et sélectionnez les références souhaitées dans la **Liste des assemblys référencés**.  
  
## Liste UIElement  
 **Address**  
 Permet de mettre à jour l'adresse web qu'une référence de service utilise pour rechercher un service.  Par exemple, pendant le développement, le service peut être hébergé sur un serveur de développement, puis transféré ultérieurement vers un serveur de production, ce qui nécessite un changement d'adresse.  
  
> [!NOTE]
>  L'élément Adresse n'est pas disponible quand la boîte de dialogue **Configurer la référence de service** est affichée à partir de la [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md).  
  
 **Niveau d'accès pour les classes générées**  
 Détermine le niveau d'accès du code pour les classes clientes WCF.  
  
> [!NOTE]
>  Pour les projets de site web, cette option a toujours la valeur `Public` et ne peut pas être modifiée.  Pour plus d'informations, voir [Troubleshooting Service References](../data-tools/troubleshooting-service-references.md).  
  
 **Générer des opérations asynchrones**  
 Détermine si les méthodes de service WCF sont appelées de façon synchrone \(valeur par défaut\) ou de façon asynchrone.  
  
 **Générer les opérations basées sur la tâche**  
 Dans le cadre de l'écriture de code asynchrone, cette option vous permet d'exploiter la bibliothèque parallèle de tâches \(TPL\) introduite dans .Net 4.  Voir [Bibliothèque parallèle de tâches](http://msdn.microsoft.com/fr-fr/library/dd460717.aspx).  
  
 **Toujours générer des contrats de message**  
 Détermine si des types de contrats de message sont générés pour un client WCF.  Pour plus d'informations sur les contrats de message, voir [Utilisation de contrats de message](../Topic/Using%20Message%20Contracts.md).  
  
 **Type de collection**  
 Spécifie le type de collection de listes pour un client WCF.  Le type par défaut est <xref:System.Array>.  
  
 **Type de collection Dictionnaire**  
 Spécifie le type de collection de dictionnaires pour un client WCF.  Le type par défaut est <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Réutiliser les types dans les assemblys référencés**  
 Détermine si un client WCF essaie de réutiliser ce qui existe déjà dans les assemblys référencés au lieu de générer de nouveaux types quand un service est ajouté ou mis à jour.  Cette option est cochée par défaut.  
  
 **Réutiliser les types dans tous les assemblys référencés**  
 Quand cette option est cochée, tous les types indiqués dans la **Liste des assemblys référencés** sont réutilisés dans la mesure du possible.  Cette option est activée par défaut.  
  
 **Réutiliser les types dans les assemblys référencés spécifiés**  
 Quand cette option est cochée, seuls les types sélectionnés dans la **Liste des assemblys référencés** sont réutilisés.  
  
 **Liste des assemblys référencés**  
 Contient la liste des assemblys référencés pour le projet ou le site web.  Quand l'option **Réutiliser les types dans les assemblys référencés spécifiés** est cochée, il est possible de sélectionner ou de désélectionner des assemblys individuels.  
  
 **Ajouter une référence web**  
 Affiche la [NIB: Add Web Reference Dialog Box](http://msdn.microsoft.com/fr-fr/bdf05776-c591-40af-bfd7-e1e2aa1e87b5).  
  
> [!NOTE]
>  Cette option doit uniquement être utilisée pour les projets qui ciblent la version 2.0 du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  Le bouton **Ajouter une référence web** est uniquement disponible quand la boîte de dialogue **Configurer la référence de service** est affichée à partir de la [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md).  
  
## Voir aussi  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)   
 [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)   
 [How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)   
 [Services Windows Communication Foundation et services de données WCF](../data-tools/configure-service-reference-dialog-box.md)   
 [Consommation de services ASMX et WCF, exemple](http://msdn.microsoft.com/fr-fr/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)