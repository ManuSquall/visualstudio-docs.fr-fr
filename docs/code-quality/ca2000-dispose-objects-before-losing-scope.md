---
title: 'CA2000 : Supprimer les objets avant la mise hors de portée'
ms.date: 05/14/2019
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 732b3d683802c50042ee40fee1549a9d247e2470
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65804973"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000 : Supprimer les objets avant la mise hors de portée

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un objet local d’un <xref:System.IDisposable> type est créé, mais l’objet n’est pas supprimé avant que toutes les références à l’objet ne soient hors de portée.

## <a name="rule-description"></a>Description de la règle

Si un objet jetable n’est pas supprimé explicitement avant que toutes les références à celle-ci soient hors de portée, l’objet sera supprimé à un moment indéterminé lorsque le garbage collector exécute le finaliseur de l’objet. Car un événement exceptionnel peut se produire et empêcher le finaliseur de l’objet à partir de l’exécution, l’objet doit être supprimé explicitement à la place.

### <a name="special-cases"></a>Cas particuliers

Même si l’objet n’est pas supprimé, la règle CA2000 ne déclenche pas d’objets locaux des types suivants :

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Transmission d’un objet d’un de ces types à un constructeur et en l’attribuant à un champ indiquent un *dispose de transfert de la propriété* pour le type qui vient d’être construit. Autrement dit, le type nouvellement construit est désormais responsable de suppression de l’objet. Si votre code passe un objet d’un de ces types à un constructeur, aucune violation de règle CA2000 se produit même si l’objet n’est pas supprimé avant toutes les références à celle-ci ne soient hors de portée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur l’objet avant que toutes les références à celle-ci soient hors de portée.

Vous pouvez utiliser la [ `using` instruction](/dotnet/csharp/language-reference/keywords/using-statement) ([ `Using` ](/dotnet/visual-basic/language-reference/statements/using-statement) en Visual Basic) pour encapsuler des objets qui implémentent <xref:System.IDisposable>. Les objets qui sont encapsulés de cette manière sont disposés automatiquement à la fin de la `using` bloc. Toutefois, les situations suivantes ne doivent pas ou ne peut pas être gérées avec un `using` instruction :

- Pour retourner un objet pouvant être supprimé, l’objet doit être construit dans une `try/finally` bloquer en dehors d’un `using` bloc.

- Ne pas initialiser les membres d’un objet pouvant être supprimé dans le constructeur d’un `using` instruction.

- Lorsque les constructeurs sont protégés par le Gestionnaire d’exceptions qu’un seul sont imbriqués dans le [partie d’acquisition d’un `using` instruction](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement), l’objet créé par le constructeur imbriqué jamais peut entraîner une défaillance dans le constructeur externe en cours de fermeture. Dans l’exemple suivant, une défaillance dans le <xref:System.IO.StreamReader> constructeur peut entraîner la <xref:System.IO.FileStream> jamais en cours de fermeture de l’objet. CA2000 signale une violation de la règle dans ce cas.

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- Objets dynamiques doivent utiliser un objet de clichés instantanés pour implémenter le modèle dispose de <xref:System.IDisposable> objets.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas d’avertissement de cette règle, sauf si :

- Vous avez appelé une méthode sur votre objet qui appelle `Dispose`, tel que <xref:System.IO.Stream.Close%2A>
- La méthode qui a déclenché l’avertissement retourne un <xref:System.IDisposable> objet qui encapsule votre objet
- La méthode d’allocation n’a pas la propriété dispose ; Autrement dit, la responsabilité de supprimer l’objet est transférée vers un autre objet ou de wrapper qui a créé dans la méthode et retourné à l’appelant

## <a name="related-rules"></a>Règles associées

- [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202 : Ne pas supprimer des objets plusieurs fois](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Exemple

Si vous implémentez une méthode qui retourne un objet pouvant être supprimé, utilisez un bloc try/finally sans un bloc catch pour vous assurer que l’objet est supprimé. En utilisant un bloc try/finally, vous autorisez des exceptions déclenché au niveau du point d’erreur et vous assurer que cet objet est supprimé.

Dans la méthode OpenPort1, l’appel pour ouvrir l’objet ISerializable SerialPort ou l’appel à SomeMethod peut échouer. Un avertissement CA2000 est déclenché sur cette implémentation.

Dans la méthode OpenPort2, deux objets SerialPort sont déclaré et défini à null :

- `tempPort`, qui est utilisée pour tester que les opérations de méthode réussissent.

- `port`, qui est utilisé pour la valeur de retour de la méthode.

Le `tempPort` est construit et ouvert dans un `try` bloc et tout autre travail obligatoire est exécuté dans le même `try` bloc. À la fin de la `try` bloc, le port ouvert est assigné à la `port` objet qui sera renvoyé et le `tempPort` objet est défini sur `null`.

Le `finally` bloc vérifie la valeur de `tempPort`. Si elle n’est pas null, une opération dans la méthode a échoué, et `tempPort` est fermé pour vous assurer que toutes les ressources sont libérées. L’objet de port retourné contiendra l’objet SerialPort ouvert si les opérations de la méthode a réussi, ou il sera null si une opération a échoué.

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

Par défaut, le compilateur Visual Basic a tous les opérateurs arithmétiques de vérification de dépassement de capacité. Par conséquent, toute opération arithmétique de Visual Basic peut lever une <xref:System.OverflowException>. Cela peut entraîner des violations des règles telles que CA2000 inattendues. Par exemple, la fonction CreateReader1 suivante produira une violation CA2000, car le compilateur Visual Basic émet une instruction pour l’addition qui pourrait lever une exception qui provoque le StreamReader ne pas être supprimé de contrôle de dépassement.

Pour résoudre ce problème, vous pouvez désactiver l’émission de contrôles de dépassement par le compilateur Visual Basic dans votre projet, ou vous pouvez modifier votre code comme dans la fonction CreateReader2 suivante.

Pour désactiver l’émission de contrôles de dépassement, cliquez sur le nom de projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**. Cliquez sur **compiler**, cliquez sur **Options avancées de compilation**, puis cochez **supprimer les contrôles de dépassement de capacité d’entier**.

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)