---
title: "Proc&#233;dure&#160;: utiliser le Concepteur de sch&#233;mas XML avec des litt&#233;raux XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: utiliser le Concepteur de sch&#233;mas XML avec des litt&#233;raux XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique décrit comment afficher un schéma associé à un littéral XML dans un projet Visual Basic.  
  
### Pour créer un projet d'application console Visual Basic  
  
1.  Démarrez Visual Studio 2010.  
  
2.  Dans le menu **Fichier**, sélectionnez **Nouveau**, puis **Projet**.La boîte de dialogue **Nouveau projet** s'affiche.Pour **Types de projets**, sélectionnez **Autres langages**, puis **Visual Basic**.Pour **Modèles**, sélectionnez Application console.Tapez ensuite `XMLLiterals` dans le champ **Nom** et un emplacement de projet dans le champ **Emplacement**.Cliquez sur **OK**.  
  
     Le nouveau projet est créé.Le projet XMLLiterals contient un fichier source Visual Basic, Module1.vb.  
  
### Pour ajouter un fichier XSD existant au projet  
  
1.  Ouvrez un nouveau fichier texte dans le Bloc\-notes. Copiez le code de l'exemple de schéma XML à partir du [Schéma de bon de commande](../xml-tools/sample-xsd-file-simple-schema.md) et collez\-le dans le fichier.  
  
2.  Enregistrez le fichier à l'emplacement de votre choix avec le nom PurchaseOrderSchema.xsd.  
  
3.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, sélectionnez **Ajouter**, puis **Élément existant**.La boîte de dialogue **Ajouterun élément existant** s'affiche.Accédez au fichier PurchaseOrderSchema.xsd, sélectionnez\-le, puis cliquez sur **Ajouter**.  
  
     Le projet XMLLiterals contient désormais deux fichiers : Module1.vb et PurchaseOrderSchema.xsd.  
  
### Pour ajouter le code Visual Basic avec un littéral XML, selon le fichier XSD inclus dans le projet  
  
1.  Remplacez le code du fichier Module1.vb par le code suivant :  
  
    ```  
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
    Module Module1  
        Sub Main()  
  
            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                 <ns:ShipTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:ShipTo>  
                                 <ns:BillTo country="US">  
                                     <ns:name>name1</ns:name>  
                                     <ns:street>street1</ns:street>  
                                     <ns:city>city1</ns:city>  
                                     <ns:state>state1</ns:state>  
                                     <ns:zip>1</ns:zip>  
                                 </ns:BillTo>  
                             </ns:PurchaseOrder>  
  
        End Sub  
    End Module  
    ```  
  
2.  Cliquez avec le bouton droit sur n'importe quel nœud XML dans un littéral XML ou une importation d'espace de noms XML, puis sélectionnez **Afficher dans l'Explorateur de schémas XML**.  
  
     L'Explorateur de schémas XML est affiché côte à côte avec un fichier Visual Basic dont le littéral XML est associé au jeu de schémas XML.