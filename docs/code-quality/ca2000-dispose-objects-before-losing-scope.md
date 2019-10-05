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
ms.openlocfilehash: 7a498a01741b86c16a52f790489dc8ce62aad06c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233239"
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

Si un objet jetable n’est pas supprimé explicitement avant que toutes les références à celui-ci soient hors de portée, l’objet sera supprimé à un moment indéterminé lorsque le garbage collector exécutera le finaliseur de l’objet. Étant donné qu’un événement exceptionnel peut se produire et empêcher l’exécution du finaliseur de l’objet, l’objet doit être supprimé explicitement à la place.

### <a name="special-cases"></a>Cas particuliers

La règle CA2000 ne se déclenche pas pour les objets locaux des types suivants, même si l’objet n’est pas supprimé :

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Passer un objet de l’un de ces types à un constructeur, puis l’assigner à un champ indique un *transfert de propriété dispose* vers le type nouvellement construit. Autrement dit, le type nouvellement construit est désormais responsable de la suppression de l’objet. Si votre code passe un objet de l’un de ces types à un constructeur, aucune violation de la règle CA2000 ne se produit même si l’objet n’est pas supprimé avant que toutes les références à celui-ci ne soient hors de portée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur l’objet avant que toutes les références à celui-ci soient hors de portée.

Vous pouvez utiliser l' [ `using` instruction](/dotnet/csharp/language-reference/keywords/using-statement) ([`Using`](/dotnet/visual-basic/language-reference/statements/using-statement) dans Visual Basic) pour encapsuler les <xref:System.IDisposable>objets qui implémentent. Les objets encapsulés de cette manière sont automatiquement supprimés à la fin du `using` bloc. Toutefois, les situations suivantes ne doivent pas ou ne peuvent pas être `using` gérées à l’aide d’une instruction :

- Pour retourner un objet jetable, l’objet doit être construit dans `try/finally` un bloc en dehors `using` d’un bloc.

- N’initialisez pas les membres d’un objet jetable dans le constructeur d' `using` une instruction.

- Lorsque des constructeurs protégés par un seul gestionnaire d’exceptions sont imbriqués dans la [partie d’acquisition d’une `using` instruction](/dotnet/csharp/language-reference/language-specification/statements#the-using-statement), un échec dans le constructeur externe peut entraîner l’objet créé par le constructeur imbriqué jamais fermé. Dans l’exemple suivant, un échec dans le <xref:System.IO.StreamReader> constructeur peut entraîner la fermeture <xref:System.IO.FileStream> de l’objet. CA2000 signale une violation de la règle dans ce cas.

   ```csharp
   using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
   { ... }
   ```

- Les objets dynamiques doivent utiliser un objet Shadow pour implémenter le modèle <xref:System.IDisposable> de suppression d’objets.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez pas un avertissement de cette règle, sauf si :

- Vous avez appelé une méthode sur votre objet qui appelle `Dispose`, telle que<xref:System.IO.Stream.Close%2A>
- La méthode qui a déclenché l’avertissement retourne <xref:System.IDisposable> un objet qui encapsule votre objet
- La méthode d’allocation n’a pas la propriété dispose ; autrement dit, la responsabilité de supprimer l’objet est transférée à un autre objet ou wrapper créé dans la méthode et retourné à l’appelant

## <a name="related-rules"></a>Règles associées

- [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)
- [CA2202 Ne pas supprimer des objets plusieurs fois](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Exemple

Si vous implémentez une méthode qui retourne un objet jetable, utilisez un bloc try/finally sans bloc catch pour vous assurer que l’objet est supprimé. En utilisant un bloc try/finally, vous autorisez le déclenchement d’exceptions au niveau du point d’erreur et assurez-vous que cet objet est supprimé.

Dans la méthode OpenPort1, l’appel permettant d’ouvrir l’objet ISerializable SerialPort ou l’appel à SomeMethod peut échouer. Un avertissement CA2000 est déclenché pour cette implémentation.

Dans la méthode OpenPort2, deux objets SerialPort sont déclarés et ont la valeur NULL :

- `tempPort`, qui est utilisé pour vérifier que les opérations de la méthode ont été correctement effectuées.

- `port`, qui est utilisé pour la valeur de retour de la méthode.

La `tempPort` est construite et ouverte dans un `try` bloc, et tout autre travail requis est effectué dans le même `try` bloc. `try` À la fin du bloc, le port ouvert est assigné à l' `port` objet qui sera retourné et `null`l’objet a `tempPort` la valeur.

Le `finally` bloc vérifie la valeur de `tempPort`. Si la valeur n’est pas null, une opération dans la méthode a échoué `tempPort` et est fermée pour s’assurer que toutes les ressources sont libérées. L’objet de port retourné contiendra l’objet SerialPort ouvert si les opérations de la méthode ont réussi, ou elle sera null en cas d’échec d’une opération.

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

Par défaut, le compilateur de Visual Basic a tous les opérateurs arithmétiques qui vérifient le dépassement de capacité. Par conséquent, toute opération arithmétique de Visual Basic peut <xref:System.OverflowException>lever une. Cela peut entraîner des violations inattendues dans des règles telles que CA2000. Par exemple, la fonction CreateReader1 suivante produira une violation CA2000, car le compilateur Visual Basic émet une instruction de vérification de dépassement pour l’ajout qui pourrait lever une exception qui provoquerait la suppression de StreamReader.

Pour résoudre ce problème, vous pouvez désactiver l’émission de contrôles de dépassement de capacité par le compilateur Visual Basic dans votre projet, ou vous pouvez modifier votre code comme dans la fonction CreateReader2 suivante.

Pour désactiver l’émission de contrôles de dépassement de capacité, cliquez avec le bouton droit sur le nom du projet dans Explorateur de solutions puis cliquez sur **Propriétés**. Cliquez sur **compiler**, sur **Options avancées de compilation**, puis activez la case à cocher Supprimer les contrôles de dépassement sur les **entiers**.

[!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)