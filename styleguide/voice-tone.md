# <a name="voice-and-tone-guidelines"></a>Instructions liées à la voix et au ton

Les développeurs liront vos documents pour découvrir .NET Core et l’utiliser dans leurs tâches courantes.
Votre objectif est de créer une documentation utile au lecteur. Nos instructions vont dans ce sens. Notre guide de style contient quatre recommandations :
- [Utiliser le ton de la conversation](#use-a-conversational-tone)
- [Écrire à la deuxième personne](#write-in-2nd-person)
- [Utiliser la voix active](#use-active-voice)
- [Cibler un niveau de lecture de CM2](#target-a-fifth-grade-reading-level)

Vous verrez des exemples de chacune de ces recommandations à mesure que vous lirez ce guide de style. Nous avons rédigé ce guide conformément aux instructions pour vous fournir des exemples à suivre lors de l’élaboration de la documentation pour .NET Core. Nous fournissons également des exemples très différents pour que vous ayez un aperçu des articles quand vous ne suivez pas nos instructions.

## <a name="details-on-each-guideline"></a>Détails sur chaque instruction

### <a name="use-a-conversational-tone"></a>Utiliser le ton de la conversation
#### <a name="appropriate-style"></a>Style approprié :
Nous voulons que notre documentation adopte le ton de la conversation. Vous devez avoir le sentiment d’avoir une discussion avec l’auteur quand vous lisez nos didacticiels ou explications.
Votre expérience en tant que lecteur doit être informelle et instructive, et du domaine de la conversation. Vous devez avoir l’impression d’écouter l’auteur vous décrire les concepts.

#### <a name="inappropriate-style"></a>Style inapproprié :
N’importe qui peut voir la différence entre le style d’une conversation et celui d’une approche plus académique de sujets techniques. Ces ressources sont très utiles, mais les auteurs ont écrit ces articles dans un style très différent de celui de notre documentation. Quand vous lisez une revue académique, vous constatez que le ton et le style d’écriture sont très différents.
Il peut vous sembler que vous lisez un compte rendu ennuyeux d’un sujet très aride.  

Le premier paragraphe ci-dessus suit notre recommandation d’adopter le style de la conversation. Le second est un style plus académique. Vous voyez immédiatement la différence. 

### <a name="write-in-second-person"></a>Écrire à la deuxième personne
#### <a name="appropriate-style"></a>Style approprié :
Vous devez écrire vos articles comme si vous parliez directement au lecteur. Vous devez souvent utiliser la deuxième personne (comme je viens de le faire dans ces deux phrases). La deuxième personne ne signifie pas toujours d’utiliser le mot « vous ». Écrivez directement au lecteur. Écrivez des phrases à l’impératif.
Dites à votre lecteur ce qu’il doit apprendre.

#### <a name="inappropriate-style"></a>Style inapproprié : 
Un auteur peut également choisir d’écrire à la troisième personne. Dans ce modèle, un auteur doit trouver un pronom ou un nom à utiliser quand il fait référence au lecteur. Un lecteur peut souvent trouver ce style à la troisième personne moins convivial et agréable à lire.

Le premier paragraphe suit notre style recommandé. Le second utilise la troisième personne. Écrivez à la deuxième personne. Vous avez probablement trouvé cela beaucoup plus facile à lire.

### <a name="use-active-voice"></a>Utiliser la voix active

Écrivez vos articles à la voix active. La voix active signifie que le sujet de la phrase effectue l’action (le verbe) de cette phrase. Elle s’oppose à la voix passive, où la phrase est organisée de telle manière que le sujet de la phrase est l’objet de l’action. Comparez ces deux exemples :

>Le compilateur a transformé le code source en un fichier exécutable.

>Le code source a été transformé en un fichier exécutable par le compilateur.

La première phrase utilise la voix active. La seconde phrase a été écrite à la voix passive.
(Ces deux phrases fournissent un autre exemple de chaque style).

Nous recommandons la voix active, car elle est plus lisible. La voix passive peut être plus difficile à lire.

### <a name="target-a-fifth-grade-reading-level"></a>Cibler un niveau de lecture de CM2

Nous fournissons cette instruction finale, car un grand nombre de nos lecteurs ne sont pas de langue maternelle anglaise.
Vos articles s’adressent à un public international. Tenez compte du fait que les lecteurs n’ont peut-être pas tous le vocabulaire anglais que vous possédez.

Vous écrivez néanmoins pour des spécialistes techniques. Vous pouvez supposer que vos lecteurs ont des connaissances en programmation et le vocabulaire spécifique des termes associés. Les termes programmation orientée objet, classe, objet, fonction et méthode seront tous familiers. Toutefois, les personnes qui lisent vos articles n’ont pas toutes un diplôme officiel en informatique. Des termes comme « idempotent » doivent probablement être définis si vous les utilisez :

>La méthode Close() est idempotent, ce qui signifie que vous pouvez l’appeler plusieurs fois et l’effet est le même que si vous l’aviez appelée une seule fois.
