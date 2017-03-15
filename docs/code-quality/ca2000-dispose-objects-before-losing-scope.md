---
title: "CA2000 : Supprimez les objets avant d&#39;&#234;tre hors de port&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2000"
  - "Dispose objects before losing scope"
  - "DisposeObjectsBeforeLosingScope"
helpviewer_keywords: 
  - "CA2000"
  - "DisposeObjectsBeforeLosingScope"
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2000 : Supprimez les objets avant d&#39;&#234;tre hors de port&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|Catégorie|Microsoft.Reliability|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un objet local d'un type <xref:System.IDisposable> est créé, mais n'est pas supprimé avant que toutes les références à celui\-ci se trouvent hors de portée.  
  
## Description de la règle  
 Si un objet supprimable n'est pas supprimé explicitement avant que toutes les références s'y rapportant ne soient hors de portée, cet objet sera supprimé à un moment indéterminé lorsque le Garbage Collector exécutera le finaliseur sur l'objet.  Il est préférable que l'objet soit supprimé explicitement, car un événement exceptionnel peut se produire, empêchant l'exécution du finaliseur de l'objet.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur l'objet avant que toutes les références à ce dernier ne se trouvent hors de portée.  
  
 Notez que vous pouvez utiliser l'instruction `using` \(`Using` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) pour inclure dans un wrapper les objets qui implémentent `IDisposable`.  Les objets inclus dans un wrapper de cette manière seront supprimés automatiquement à la fin du bloc `using`.  
  
 Dans les situations suivantes, l'instruction using n'est pas suffisante pour protéger des objets IDisposable et peut provoquer le déclenchement de CA2000.  
  
-   Le retour d'un objet jetable requiert que l'objet soit construit dans un bloc try\/finally en dehors d'un bloc using.  
  
-   L'initialisation des membres d'un objet jetable ne doit pas être faite dans le constructeur d'une instruction using.  
  
-   Constructeurs d'imbrication qui sont protégés uniquement par un gestionnaire d'exceptions.  Par exemple :  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     provoque le déclenchement du CA2000 parce qu'un échec dans la construction de l'objet StreamReader peut empêcher la fermeture de l'objet FileStream.  
  
-   Les objets dynamiques doivent utiliser un objet shadow pour implémenter le modèle Dispose des objets IDisposable.  
  
## Quand supprimer les avertissements  
 Ne supprimez pas les avertissements faisant référence à cette règle à moins que vous ayez appelé une méthode sur votre objet qui appelle `Dispose`, comme <xref:System.IO.Stream.Close%2A>, ou si la méthode qui a déclenché l'avertissement retourne objet IDisposable qui englobe votre objet.  
  
## Règles connexes  
 [CA2213 : Les champs pouvant être supprimés doivent l'être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202 : Ne pas supprimer des objets plusieurs fois](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## Exemple  
 Si vous implémentez une méthode qui rétablit un objet jetable, utilisez un bloc try\/finally sans un bloc catch pour s'assurer que l'objet est jeté.  En utilisant un bloc try\-finally, vous permettez aux exceptions d'être levées et garantissez la suppression de l'objet.  
  
 Dans la méthode OpenPort1, l'appel pour ouvrir l'objet ISerializable SerialPort ou l'appel à SomeMethod peut échouer.  Un avertissement CA2000 est déclenché sur cette implémentation.  
  
 Dans la méthode OpenPort2, deux objets SerialPort sont déclarés et définis à null :  
  
-   `tempPort`, utilisé pour tester que les opérations de méthode réussissent.  
  
-   `port`, utilisé pour la valeur de retour de la méthode.  
  
 Le `tempPort` est construit et ouvert dans un bloc `try`, et tout autre travail obligatoire est exécuté dans le même bloc `try`.  À la fin du bloc `try`, le port ouvert est assigné à l'objet `port` qui sera retourné et l'objet `tempPort` a la valeur `null`.  
  
 Le bloc `finally` vérifie la valeur de `tempPort`.  Si sa valeur n'est pas null, une opération dans la méthode a échoué, et `tempPort` est fermé pour s'assurer que toutes les ressources sont libérées.  L'objet de port retourné contiendra l'objet SerialPort ouvert si les opérations de la méthode ont réussi, ou il sera null si une opération a échoué.  
  
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-cs[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/CSharp/ca2000-dispose-objects-before-losing-scope_1.cs)]  
  
## Exemple  
 Par défaut, le compilateur de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] vérifie le dépassement de capacité de tous les opérateurs arithmétiques de vérifier.  Par conséquent, n'importe quelle opération arithmétique de Visual Basic pourrait lever une exception <xref:System.OverflowException>.  Cela pourrait mener à des violations inattendues de règles telles que CA2000.  Par exemple, la fonction CreateReader1 suivante produira une violation CA2000 parce que le compilateur Visual Basic émet une instruction de contrôle de dépassement pour l'addition qui pourrait lever une exception qui provoquerait que le StreamReader ne soit pas supprimé.  
  
 Pour résoudre ceci, vous pouvez désactiver l'émission de contrôles de dépassement par le compilateur Visual Basic dans votre projet ou vous pouvez modifier votre code comme la fonction CreateReader2 suivante.  
  
 Pour désactiver l'émission de contrôles de dépassement, cliquez avec le bouton droit sur le nom du projet dans l'Explorateur de solutions puis cliquez sur **Propriétés**.  Cliquez sur **Compiler**, cliquez sur **Options avancées de compilation**, puis sélectionnez **Supprimer les contrôles de dépassement sur les entiers**.  
  
 [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  
  
## Voir aussi  
 <xref:System.IDisposable>   
 [Modèle de suppression](../Topic/Dispose%20Pattern.md)