---
title: "D&#233;pannage des exceptions&#160;: System.Security.SecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSecurity"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "System.Security.SecurityException (classe)"
  - "SecurityException (classe)"
ms.assetid: 7679ef74-dd15-439f-bfeb-0fb45f8b2373
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Security.SecurityException
Une exception <xref:System.Security.SecurityException> est levée lors de la détection d'une erreur de sécurité.  
  
## Conseils associés  
 Définissez le niveau d'autorisation de l'assembly via la page de propriétés.  
 Pour plus d'informations, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.SqlPermissionLevel%2A>.  
  
 Stockez les données d'application dans un stockage isolé.  
 Le stockage isolé est un stockage de données qui offre un isolement et une sécurité en définissant des méthodes standardisées pour associer du code à des données enregistrées. Pour plus d’informations, consultez [Stockage isolé](../Topic/Isolated%20Storage.md).  
  
 Si vous utilisez <xref:System.Windows.Forms.OpenFileDialog>, utilisez la méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> pour ouvrir ou enregistrer un fichier.  
 Cela permet à l'application de s'exécuter dans une situation d'un niveau de confiance partiel.  
  
 Assurez\-vous que l'application lit et écrit dans les journaux des événements existants sur l'ordinateur local.  
 L'application peut ne pas disposer des autorisations suffisantes pour créer des journaux ou écrire sur des ordinateurs non locaux.  
  
 Lorsque vous appelez des bibliothèques non managées, utilisez les bibliothèques managées équivalentes.  
 Une API équivalente peut exister dans le .NET Framework. Pour plus d'informations, consultez [Troubleshooting Interoperability](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability).  
  
 Utilisez des fenêtres sécurisées.  
 L'énumération <xref:System.Security.Permissions.UIPermissionWindow> spécifie les types de fenêtres que le code peut utiliser.  
  
 Autorisez les utilisateurs à imprimer par le biais du composant <xref:System.Windows.Forms.PrintDialog>.  
 Cela permet à l'application de s'exécuter dans une situation d'un niveau de confiance partiel. Pour plus d'informations, consultez <xref:System.Windows.Forms.PrintDialog>.  
  
 Imprimez sur l'imprimante par défaut.  
 Cela permet à l'application de s'exécuter dans une situation d'un niveau de confiance partiel. Vous essayez peut\-être d'accéder à une imprimante pour laquelle vous ne disposez par de droits.  
  
 Récupérez les données du serveur Web ayant servi au déploiement des données.  
 Cela permet à l'application de s'exécuter dans une situation d'un niveau de confiance partiel.  
  
 Lors du déploiement d'une solution Office, vérifiez que vous répondez à toutes les conditions de sécurité requises.  
 Pour plus d'informations, consultez [Considérations spécifiques sur la sécurité pour les solutions Office](/office-dev/office-dev/specific-security-considerations-for-office-solutions).  
  
 Si un assembly qui implémente l'objet de sécurité personnalisé fait référence à d'autres assemblys, ajoutez les assemblys référencés à la liste des assemblys de confiance totale.  
 Pour plus d'informations, consultez [Caspol.exe \(Code Access Security Policy Tool\)](../Topic/Caspol.exe%20\(Code%20Access%20Security%20Policy%20Tool\).md).  
  
## Voir aussi  
 <xref:System.Security.SecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)