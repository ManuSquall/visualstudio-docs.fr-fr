---
title: "CA2000 : Supprimez les objets avant d'être hors de portée"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b492324b87bfc25741492669b7c659c43fc9765
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000 : Supprimez les objets avant d'être hors de portée
|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un objet local d’un <xref:System.IDisposable> type est créé, mais l’objet n’est pas supprimé avant que toutes les références à l’objet soient hors de portée.

## <a name="rule-description"></a>Description de la règle
 Si un objet supprimable n’est pas supprimé explicitement avant que toutes les références à lui soient hors de portée, l’objet sera supprimé à un moment indéterminé lorsque le garbage collector s’exécute le finaliseur de l’objet. Car un événement exceptionnel peut se produire et empêcher le finaliseur de l’objet en cours d’exécution, l’objet doit être supprimé explicitement à la place.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur l’objet avant que toutes les références à lui soient hors de portée.

 Notez que vous pouvez utiliser la `using` instruction (`Using` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) pour encapsuler les objets qui implémentent `IDisposable`. Objets encapsulés de cette manière seront supprimés automatiquement à la fin de la `using` bloc.

 Voici quelques situations où l’à l’aide d’instruction n’est pas suffisante pour protéger des objets IDisposable et peut provoquer CA2000 se produise.

-   Renvoi d’un objet supprimable requiert que l’objet est construit dans un bloc try/finally en dehors d’un à l’aide de bloc.

-   L’initialisation des membres d’un objet supprimable ne doit pas être exécutée dans le constructeur d’une utilisant l’instruction.

-   Constructeurs d’imbrication qui sont protégés uniquement par un gestionnaire d’exceptions. Par exemple :

    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     provoque la CA2000 parce qu’un échec dans la construction de l’objet StreamReader peut entraîner l’objet FileStream jamais en cours de fermeture.

-   Objets dynamiques doivent utiliser un objet de clichés instantanés pour implémenter le modèle de suppression des objets IDisposable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle, sauf si vous avez appelé une méthode sur votre objet qui appelle `Dispose`, tel que <xref:System.IO.Stream.Close%2A>, ou si la méthode qui a déclenché l’avertissement retourne un objet IDisposable encapsule votre objet.

## <a name="related-rules"></a>Règles associées
 [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202 : Ne pas supprimer des objets plusieurs fois](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Exemple
 Si vous implémentez une méthode qui retourne un objet pouvant être supprimé, utilisez un bloc try/finally sans un bloc catch pour vous assurer que l’objet est supprimé. En utilisant un bloc try/finally, vous autorisez des exceptions être déclenché sur le point d’erreur et assurez-vous que cet objet est supprimé.

 Dans la méthode OpenPort1, l’appel pour ouvrir l’objet ISerializable SerialPort ou l’appel à SomeMethod peut échouer. Un avertissement CA2000 est déclenché sur cette implémentation.

 Dans la méthode OpenPort2, deux objets SerialPort sont déclaré et défini à null :

-   `tempPort`, qui est utilisé pour tester que les opérations de méthode réussissent.

-   `port`, qui est utilisé pour la valeur de retour de la méthode.

 Le `tempPort` est construit et ouvert dans un `try` bloc, ainsi que tout autre travail obligatoire est exécuté dans le même `try` bloc. À la fin de la `try` bloc, le port ouvert est assigné à la `port` objet qui sera renvoyé et le `tempPort` objet a la valeur `null`.

 Le `finally` bloc vérifie la valeur de `tempPort`. Si elle n’est pas null, une opération dans la méthode a échoué, et `tempPort` est fermé pour s’assurer que toutes les ressources sont libérées. L’objet de port retourné contiendra l’objet SerialPort ouvert si les opérations de la méthode a réussi, ou il sera null si une opération a échoué.

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function


Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If


   End Try

   Return port

End Function
```

## <a name="example"></a>Exemple
 Par défaut, le [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilateur a de dépassement de capacité de validation de tous les opérateurs arithmétiques. Par conséquent, toute opération arithmétique de Visual Basic peut lever une <xref:System.OverflowException>. Cela peut entraîner des violations inattendues de règles telles que CA2000. Par exemple, la fonction CreateReader1 suivante produira une violation CA2000 parce que le compilateur Visual Basic émet une instruction pour l’addition qui pourrait lever une exception susceptible d’empêcher le StreamReader ne pas être supprimé de contrôle de dépassement de capacité.

 Pour résoudre ce problème, vous pouvez désactiver l’émission de contrôles de dépassement par le compilateur Visual Basic dans votre projet, ou vous pouvez modifier votre code comme dans la fonction CreateReader2 suivante.

 Pour désactiver l’émission de contrôles de dépassement, cliquez sur le nom du projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**. Cliquez sur **compiler**, cliquez sur **Options avancées de compilation**, puis **supprimer les contrôles de dépassement de capacité d’entier**.

  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Voir aussi
 <xref:System.IDisposable> [Modèle de suppression](/dotnet/standard/design-guidelines/dispose-pattern)