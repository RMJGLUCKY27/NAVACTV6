# NAVEGATION-ACTV6
Este proyecto implementa un sistema de navegación basado en NavMesh en Unity, utilizando AI Navigation, Input System y Raycasts para permitir la interacción del usuario con un agente de navegación en un entorno 3D.

Directivas de uso (using):
Se importan los espacios de nombres necesarios:

UnityEngine: Proporciona funcionalidades básicas de Unity.
UnityEngine.AI: Permite utilizar la inteligencia artificial de navegación (NavMesh) para mover agentes.
UnityEngine.InputSystem: Ofrece soporte para el nuevo sistema de entrada, facilitando el manejo de dispositivos como el mouse.
Declaración de la clase y variables:
La clase Player hereda de MonoBehaviour, lo que indica que es un componente que se puede adjuntar a un GameObject en Unity. Dentro de la clase, se definen:

mainCamera: Una referencia a la cámara principal, marcada con [SerializeField] para que pueda configurarse desde el Inspector sin necesidad de ser pública.
agent: Una variable privada de tipo NavMeshAgent que representa el agente de navegación encargado de moverse por el escenario.
Método Start():
En el método Start(), se inicializa la variable agent obteniendo el componente NavMeshAgent del GameObject al que está asociado este script. Esto asegura que el agente de navegación esté listo para usarse cuando se ejecute el juego.

Método Update():
Dentro de Update(), que se ejecuta en cada frame, se realiza lo siguiente:

Detección del clic: Se verifica si el botón izquierdo del mouse fue presionado en ese frame mediante Mouse.current.leftButton.wasPressedThisFrame.
Generación del rayo: Si se detecta el clic, se crea un rayo partiendo desde la posición de la cámara hacia la dirección correspondiente al punto donde se hizo clic en la pantalla. Esto se realiza con mainCamera.ScreenPointToRay(Mouse.current.position.ReadValue()).
Detección de colisión con el mundo: Se lanza un rayo en la escena utilizando Physics.Raycast(). Si el rayo impacta contra algún objeto (por ejemplo, el suelo), la variable hit almacena la información del punto de impacto.
Actualización del destino del agente: Finalmente, se actualiza el destino del NavMeshAgent llamando a agent.SetDestination(hit.point). Esto hace que el agente se mueva automáticamente hacia el punto donde el usuario hizo clic.
