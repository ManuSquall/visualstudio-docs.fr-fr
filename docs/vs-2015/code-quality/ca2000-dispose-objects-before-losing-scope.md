---
title: 'CA2000 : supprimez les objets avant de perdre l’étendue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e3de3246980ead0b20d471321a9696451aed81ac
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534769"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000 : Supprimer les objets avant la mise hors de portée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Category|Microsoft. fiabilité|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un objet local d’un <xref:System.IDisposable> type est créé, mais l’objet n’est pas supprimé avant que toutes les références à l’objet ne soient hors de portée.

## <a name="rule-description"></a>Description de la règle
 Si un objet jetable n’est pas supprimé explicitement avant que toutes les références à celui-ci soient hors de portée, l’objet sera supprimé à un moment indéterminé lorsque le garbage collector exécutera le finaliseur de l’objet. Étant donné qu’un événement exceptionnel peut se produire et empêcher l’exécution du finaliseur de l’objet, l’objet doit être supprimé explicitement à la place.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez <xref:System.IDisposable.Dispose%2A> sur l’objet avant que toutes les références à celui-ci soient hors de portée.

 Notez que vous pouvez utiliser l' `using` instruction ( `Using` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) pour encapsuler les objets qui implémentent `IDisposable` . Les objets encapsulés de cette façon seront automatiquement supprimés à la fermeture du `using` bloc.

 Voici quelques situations dans lesquelles l’instruction using n’est pas suffisante pour protéger les objets IDisposable et peut entraîner l’apparition de CA2000.

- Le retour d’un objet jetable requiert que l’objet soit construit dans un bloc try/finally en dehors d’un bloc using.

- L’initialisation des membres d’un objet jetable ne doit pas être effectuée dans le constructeur d’une instruction using.

- Imbrication des constructeurs qui sont protégés par un seul gestionnaire d’exceptions. Par exemple,

    ```
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     provoque l’apparition de CA2000 en raison de l’échec de la fermeture d’un objet StreamReader dans la construction de l’objet StreamReader.

- Les objets dynamiques doivent utiliser un objet Shadow pour implémenter le modèle dispose d’objets IDisposable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle, sauf si vous avez appelé une méthode sur votre objet qui appelle `Dispose` , tel que <xref:System.IO.Stream.Close%2A> , ou si la méthode qui a déclenché l’avertissement retourne un objet IDisposable encapsule votre objet.

## <a name="related-rules"></a>Règles associées
 [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202 : Ne pas supprimer d'objets plusieurs fois](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>Exemple
 Si vous implémentez une méthode qui retourne un objet jetable, utilisez un bloc try/finally sans bloc catch pour vous assurer que l’objet est supprimé. En utilisant un bloc try/finally, vous autorisez le déclenchement d’exceptions au niveau du point d’erreur et assurez-vous que cet objet est supprimé.

 Dans la méthode OpenPort1, l’appel permettant d’ouvrir l’objet ISerializable SerialPort ou l’appel à SomeMethod peut échouer. Un avertissement CA2000 est déclenché pour cette implémentation.

 Dans la méthode OpenPort2, deux objets SerialPort sont déclarés et ont la valeur NULL :

- `tempPort`, qui est utilisé pour vérifier que les opérations de la méthode ont été correctement effectuées.

- `port`, qui est utilisé pour la valeur de retour de la méthode.

  La `tempPort` est construite et ouverte dans un `try` bloc, et tout autre travail requis est effectué dans le même `try` bloc. À la fin du `try` bloc, le port ouvert est assigné à l' `port` objet qui sera retourné et l' `tempPort` objet a la valeur `null` .

  Le `finally` bloc vérifie la valeur de `tempPort` . Si la valeur n’est pas null, une opération dans la méthode a échoué et `tempPort` est fermée pour s’assurer que toutes les ressources sont libérées. L’objet de port retourné contiendra l’objet SerialPort ouvert si les opérations de la méthode ont réussi, ou elle sera null en cas d’échec d’une opération.

  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]

## <a name="example"></a>Exemple
 Par défaut, le [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilateur a tous les opérateurs arithmétiques qui vérifient le dépassement de capacité. Par conséquent, toute opération arithmétique de Visual Basic peut lever une <xref:System.OverflowException> . Cela peut entraîner des violations inattendues dans des règles telles que CA2000. Par exemple, la fonction CreateReader1 suivante produira une violation CA2000, car le compilateur Visual Basic émet une instruction de vérification de dépassement pour l’ajout qui pourrait lever une exception qui provoquerait la suppression de StreamReader.

 Pour résoudre ce problème, vous pouvez désactiver l’émission de contrôles de dépassement de capacité par le compilateur Visual Basic dans votre projet, ou vous pouvez modifier votre code comme dans la fonction CreateReader2 suivante.

 Pour désactiver l’émission de contrôles de dépassement de capacité, cliquez avec le bouton droit sur le nom du projet dans Explorateur de solutions puis cliquez sur **Propriétés**. Cliquez sur **compiler**, sur **Options avancées de compilation**, puis activez la case à cocher Supprimer les contrôles de dépassement sur les **entiers**.

<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->

## <a name="see-also"></a>Voir aussi
 <xref:System.IDisposable>[Modèle de suppression](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)