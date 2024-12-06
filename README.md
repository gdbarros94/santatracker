Santa Tracker
O Santa Tracker é um aplicativo web interativo que mostra a jornada do Papai Noel pelo mundo usando Leaflet.js para mapas e simulações baseadas em lógica de programação. O projeto é uma ferramenta educacional para demonstrar cálculo matemático, lógica complexa e integração de tecnologias frontend.

Demonstração
Acesse a aplicação no site oficial:
Santa Tracker

📜 Descrição do Projeto
O aplicativo utiliza um mapa interativo para mostrar o progresso do Papai Noel enquanto ele viaja entre países. Ele calcula tempos de viagem e distâncias entre os locais, simulando movimento em tempo real com base em dados populacionais e geográficos.

🧩 Estrutura de Código
HTML
O HTML define a estrutura básica da aplicação:

Mapa interativo: Elemento <div> com ID map.
Inclui as bibliotecas Leaflet.js e Tailwind CSS para funcionalidades e estilos.
CSS
As configurações de estilo são feitas com:

Height do mapa (#map): Preenchendo toda a altura da janela do navegador.
Estilo de fundo: Classes do Tailwind CSS (bg-gray-900 text-white) para uma aparência moderna.
JavaScript
Configurações
javascript
Copiar código
const config = {
  speed: 5200,
  start: { lat: 75.186589, lng: -74.672401 },
  startTime: new Date('December 06, 2024 14:00:00').getTime(),
};
speed: Define a velocidade do Papai Noel (em km/h).
start: Coordenadas do Polo Norte (ponto de partida).
startTime: Data e hora em que a jornada começa.
Lista de Países
javascript
Copiar código
const countries = [
  { name: "Canada", lat: 56.1304, lng: -106.3468, population: 38000000 },
  ...
];
Cada país possui nome, coordenadas geográficas e população, usados para cálculos de tempo de viagem.
Cálculos Matemáticos
Tempo de Visita por País:

javascript
Copiar código
function calculateTimeForCountry(population) {
  const baseTime = 2; // Tempo mínimo em minutos
  const scalingFactor = 0.0001;
  return baseTime + population * scalingFactor;
}
Combina tempo base com um fator proporcional à população.

Distância entre Locais:

javascript
Copiar código
function calculateDistance(lat1, lng1, lat2, lng2) {
  const R = 6371; // Raio da Terra em km
  ...
  return R * 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
}
Fórmula haversine para calcular distâncias geográficas.

Jornada e Atualização
Preparação da Jornada:

javascript
Copiar código
function prepareJourney() {
  const journey = [];
  ...
  journey.push({
    name: country.name,
    lat: country.lat,
    lng: country.lng,
    travelTime,
  });
  ...
}
Define a rota com base nas distâncias e calcula o tempo de viagem entre os países.

Atualização de Posição:

javascript
Copiar código
function updateSantaPosition(journey) {
  const now = new Date().getTime();
  ...
  const elapsedTime = (now - config.startTime) / 3600000; // Tempo em horas
  ...
  santaMarker.setLatLng([lat, lng]);
  map.setView([lat, lng], 4);
}
Atualiza a posição do Papai Noel no mapa em tempo real.

📊 Funcionalidades
Mapa interativo: Exibe a jornada do Papai Noel com zoom ajustável.
Movimento simulado: Atualiza a posição no mapa dinamicamente.
Cálculo em tempo real: Utiliza fórmulas de distância e escalas populacionais.
Popups informativos: Mostram a posição atual e o próximo destino.

🌟 Conclusão
Este projeto é um exemplo prático de como combinar lógica de programação, manipulação de mapas e bibliotecas frontend para criar experiências interativas. Aproveite o código como base para explorar mais cálculos, animações e interatividade.
