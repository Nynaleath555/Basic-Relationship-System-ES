# 👥💕🇪🇸 Nynaleath's Basic Relationship System ES V1

«🇪🇸 Versión en español del Basic Relationship System original.

Esta versión adapta el sistema para escenarios jugados en español, manteniendo la misma lógica y funcionamiento del Basic Relationship System original.

La versión en español se actualizará siguiendo las futuras versiones de la versión original en inglés siempre que sea necesario.»

Un sistema ligero de relaciones dinámicas para AI Dungeon, diseñado para hacer que las relaciones entre los NPCs se desarrollen de forma más natural, consistente y realista.

# ✨ ¿Qué es?

Diseñé este sistema para hacer que las interacciones y relaciones entre el jugador y los NPCs sean más dinámicas y creíbles en AI Dungeon.

Uno de los problemas de las relaciones controladas por IA es que, en ocasiones, la IA puede inventar o ignorar información ya establecida para satisfacer las acciones del jugador. Incluso cuando información importante sobre un personaje ya está definida en Story Cards o Plot Components, la IA puede ocasionalmente modificarla o ignorarla por completo.

Por ejemplo, un NPC que está establecido explícitamente como gay podría sentirse atraído repentinamente por el jugador a pesar de que el género del jugador sea incompatible con su orientación, simplemente porque el jugador ha coqueteado con él. Los personajes también pueden convertirse en amigos cercanos o desarrollar sentimientos románticos después de muy pocas interacciones, sin suficiente desarrollo significativo que lo justifique.

Basic Relationship System está diseñado para ayudar a reducir estas inconsistencias.

En lugar de depender completamente de que la IA recuerde e interprete cada interacción anterior, el sistema mantiene valores de relación persistentes para cada NPC seguido y proporciona a la IA contexto adicional sobre su relación actual con el jugador.

El sistema también tiene en cuenta información del personaje como:

- Orientación sexual
- Género
- Relaciones románticas existentes
- Crushes o intereses amorosos existentes
- Hobbies
- Gustos
- Disgustos

al determinar cómo se desarrollan las relaciones.

El objetivo no es sustituir el criterio narrativo de la IA, sino proporcionarle una base más consistente sobre la que trabajar.

El sistema fue creado originalmente para 🎸 A Rising Rockstar Life 🎸 y también fue implementado en 📁 Framed, The Silent Hero y The Secrets of Millhaven

---

💡 ¿Cómo funciona?

Basic Relationship System realiza un seguimiento de dos dimensiones independientes de la relación:

👥 Amistad
Cómo positiva o negativamente se siente el NPC hacia el jugador como persona.

💕 Romance
Los sentimientos románticos del NPC hacia el jugador.

Estos valores son independientes.

Por ejemplo:

- Un NPC puede convertirse en un amigo cercano sin desarrollar sentimientos románticos.
- Un NPC puede sentir interés romántico sin ser un amigo cercano.
- El jugador puede mejorar la amistad sin aumentar automáticamente el romance.
- Los sentimientos románticos pueden desarrollarse más lentamente cuando el NPC ya tiene un crush, está enamorado, mantiene una relación o está casado.
- A un NPC puede disgustarle algo que le gusta al jugador sin que eso haga que automáticamente se vuelva hostil hacia él.
- Defender o alabar repetidamente algo que al NPC le disgusta puede deteriorar gradualmente la amistad.

Esta separación permite que las relaciones se desarrollen de una forma más natural, en lugar de seguir una progresión simple de amistad → romance.

---

# 🧠 Consistencia de los personajes

Uno de los principales objetivos del sistema es ayudar a conservar la información que ya ha sido establecida sobre los NPCs.

El sistema lee información relevante de las Story Cards de los NPCs, incluyendo:

Orientación sexual y género

La compatibilidad romántica se comprueba utilizando el género y la orientación sexual establecidos del NPC.

Si un NPC es románticamente incompatible con el jugador, el sistema impide que la relación desarrolle atracción romántica hacia el jugador.

La IA recibe instrucciones explícitas para no cambiar la sexualidad del NPC ni inventar una excepción repentina simplemente para adaptarse a las acciones románticas del jugador.

Relaciones románticas existentes

Los NPCs que ya tienen:

- Un crush
- Alguien de quien están enamorados
- Una pareja romántica
- Un cónyuge

tienen una receptividad romántica reducida hacia el jugador.

Esto hace que el desarrollo romántico sea considerablemente más difícil y tenga mayores consecuencias.

Hobbies, gustos y disgustos

El sistema también lee:

- ""Hobbies:""
- ""Likes:""
- ""Dislikes:""

de la Story Card del NPC.

Los hobbies y gustos compartidos pueden proporcionar pequeñas bonificaciones de amistad.

Simplemente mencionar algo que no le gusta a un NPC no provoca automáticamente una reacción negativa.

Sin embargo, alabar, defender o insistir repetidamente en algo que al NPC le disgusta puede reducir gradualmente la amistad.

Esto permite que las preferencias personales influyan en las relaciones sin hacer que cada desacuerdo parezca desproporcionadamente importante.

---

# 🐢 Diseñado para un desarrollo gradual de las relaciones

Basic Relationship System está diseñado para que las relaciones no tengan que cambiar drásticamente después de cada interacción.

Las pequeñas interacciones sociales producen pequeños cambios.

Las conversaciones significativas y los momentos de apoyo producen cambios mayores.

Las interacciones fuertemente negativas pueden dañar considerablemente la relación.

El romance es intencionadamente más restrictivo que la amistad y se ve afectado tanto por la situación romántica actual del NPC como por su amistad con el jugador.

El sistema no convierte aleatoriamente una amistad en romance simplemente porque dos personajes hayan interactuado muchas veces.

En su lugar, el desarrollo romántico depende principalmente de las interacciones románticas reconocidas por el sistema y del contexto establecido por la historia.

El objetivo es que la progresión de las relaciones se sienta merecida en lugar de automática.

---

# 📊 Visualización del estado de la relación

El sistema puede generar automáticamente una Story Card de Relationship Status para los NPCs seguidos.

La tarjeta muestra los valores actuales de:

👥 Amistad
💕 Romance

junto con su correspondiente nivel descriptivo de relación.

Por ejemplo:

«Friendship: 42.5 — Friend
Romance: 12.7 — Mild Attraction»

Los números mostrados en la tarjeta de Relationship Status se redondean para facilitar su lectura.

Sin embargo, el sistema mantiene y calcula internamente los valores decimales reales.

Por ejemplo, la tarjeta puede mostrar:

«Friendship: 12.4»

mientras que el valor interno puede contener una precisión decimal adicional resultado de varias bonificaciones y penalizaciones pequeñas.

Esto permite que la progresión de las relaciones sea gradual y evita que los pequeños efectos de las interacciones se pierdan simplemente porque la visualización utiliza números redondeados.

La tarjeta de Relationship Status también indica cuándo un NPC seguido está actualmente activo en la escena.

---

# 👥 Seguimiento de escenas

Basic Relationship System incluye un sistema ligero de seguimiento de escenas.

El sistema intenta determinar qué NPCs seguidos están actualmente involucrados en la escena utilizando la acción actual del jugador y el historial reciente de la historia.

Esto permite aplicar los cambios de relación al NPC con el que realmente se está interactuando, en lugar de modificar indiscriminadamente a todos los personajes seguidos.

Cuando hay varios NPCs presentes y la acción del jugador es ambigua, el sistema evita adivinar.

Por ejemplo, si hay dos NPCs presentes y el jugador escribe una acción ambigua como:

«"Les sonrío."»

el sistema no asigna automáticamente esa interacción a uno de los NPCs.

Esto ayuda a evitar cambios de relación no deseados.

El seguimiento de escenas también permite que un NPC permanezca activo durante unos cuantos turnos después de ser detectado, haciendo que las conversaciones e interacciones normales se sientan más continuas.

---

🔌 Compatibilidad

Basic Relationship System está diseñado como un sistema independiente.

No requiere Inner Self ni depende de Inner Self para funcionar.

Es compatible con Inner Self, pero no ha sido probado con otros scripts de la comunidad.

Por lo tanto, la compatibilidad con otros scripts puede variar dependiendo de cómo dichos scripts modifiquen Story Cards, Context, Input, Output o State.

---

# 📦 Instalación

Requisitos

- Modo de edición de scripts de AI Dungeon
- Conocimientos básicos sobre scripting en AI Dungeon
- Story Cards de NPCs que contengan la información requerida por el sistema

Configuración

1. Copia la Library de Basic Relationship System en tu Library.
2. Copia el Input de Basic Relationship System en tu bloque Input.
3. Copia el Context de Basic Relationship System en tu bloque Context.
4. Copia el Output de Basic Relationship System en tu bloque Output.
5. Crea o utiliza la Story Card "Basic REL v2 — Relationship Status Configuration".
6. Introduce en la tarjeta de configuración los nombres exactos de los NPCs que quieres seguir.
7. Inicia tu escenario.

El sistema creará y actualizará automáticamente las tarjetas de Relationship Status de los NPCs seguidos.

Para obtener una mejor compatibilidad, los nombres de los personajes deberían coincidir con los nombres utilizados en sus Story Cards.

---

# ⚙️ Configuración

La tarjeta de configuración permite especificar qué NPCs deben tener una tarjeta de Relationship Status visible.

Ejemplo:

Tracked Characters:
Elio, Sarah, Lucien

Solo los personajes incluidos en la tarjeta de configuración recibirán una tarjeta de Relationship Status visible.

El sistema de relaciones puede seguir manteniendo datos internos de relación para otros NPCs reconocidos.

Puedes editar la tarjeta de configuración en cualquier momento durante una aventura.

---

# 📜 Estados de relación

## 👥 Amistad

Enemy
→ Persona Non Grata
→ Neutral
→ Acquaintance
→ Friend
→ Good Friend
→ Best Friends

## 💕 Romance

No Romantic Interest
→ Mild Attraction
→ Romantic Interest
→ Falling in Love
→ Sweethearts
→ Soulmates

Estas etiquetas se utilizan principalmente para proporcionar a la IA una descripción significativa del estado actual de la relación, en lugar de mostrar únicamente los valores numéricos.

---

# 🎯 Uso recomendado

Basic Relationship System está especialmente indicado para:

- 👥 Escenarios con múltiples NPCs
- 💕 Escenarios centrados en el romance y las relaciones
- 🐢 Desarrollo lento o gradual de las relaciones
- 🎭 Historias centradas en los personajes
- 🏠 Escenarios slice-of-life
- 📖 Historias en las que el jugador puede desarrollar relaciones con los NPCs
- 🧠 Escenarios donde la personalidad de los NPCs y la información establecida sobre ellos son importantes
- ❤️ Escenarios donde los NPCs deben reaccionar de forma diferente dependiendo de su sexualidad, situación romántica, preferencias e interacciones anteriores

Puede resultar especialmente útil en escenarios donde el jugador tiene libertad para interactuar con muchos NPCs y el autor quiere que esas relaciones se desarrollen de forma independiente.

Puede resultar menos útil para escenarios donde:

- Las relaciones son intencionadamente instantáneas.
- La sexualidad o situación romántica de los NPCs no es relevante.
- Las relaciones están completamente predeterminadas.
- No se espera que el jugador desarrolle relaciones con los NPCs.
- La progresión de las relaciones está completamente controlada mediante elecciones explícitamente programadas.

---

# 📜 Licencia

Este proyecto está publicado bajo la licencia MIT.

Eres libre de:

- Utilizar el sistema en tus propios escenarios.
- Modificarlo.
- Integrarlo en tus propios proyectos.
- Publicar escenarios que lo contengan.
- Redistribuir versiones modificadas.

No es obligatorio dar crédito, pero se agradece enormemente.

Si utilizas o modificas este sistema en tu escenario, me encantaría que me acreditaras con una mención y, si es posible, con un enlace a este repositorio o a mi página de AI Dungeon.

Atribución

Basic Relationship System
Creado por Nynaleath

---

❤️ Créditos

Creado por Nynaleath.

Desarrollado originalmente para 🎸 A Rising Rockstar Life 🎸.

¡Gracias por probar Basic Relationship System!

Si lo utilizas en uno de tus escenarios, me encantaría ver lo que haces con él — y cualquier crédito siempre será bien recibido.
