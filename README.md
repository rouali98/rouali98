 ## Hi 👋, I'm [Ouali Rida!](https://Ouali98.github.io)

<!--
**Ouali98/Ouali98** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
<p align = "center">
  <a href="https://github.com/Ouali98">
    <img align="center" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Ouali98&theme=dark">
  </a>
  <a href="https://github.com/Ouali98">
    <img align="center" src="https://github-readme-stats.vercel.app/api?username=Ouali98&show_icons=true&theme=dark&line_height=30" alt="Ankit's github stats"/>
  </a>
</p>

import queryString from 'query-string'
import { Formik } from 'formik'
import { useState } from 'react'
type Query = {
  login: string
  cursus?: string
  email?: string
  dark?: string
  leet_logo?: string
  forty_two_network_logo?: string
}
type ProfileCardProps = {
  login: string
  cursus: string
  showEmail: boolean
  darkTheme: boolean
  hideLeetLogo: boolean
  hideFortyTwoNetworkLogo: boolean
}
export default function ProfileCardGenerator() {
  const [cardImage, setCardImage] = useState(
    '/api/profile?login=ozaazaa&cursus=42&email=hide'
  )
  const initialValues: ProfileCardProps = {
    login: 'ozaazaa',
    cursus: '42',
    showEmail: false,
    darkTheme: false,
    hideLeetLogo: false,
    hideFortyTwoNetworkLogo: false,
  }
  function generateProfileCard({
    login,
    cursus,
    showEmail,
    darkTheme,
    hideLeetLogo,
    hideFortyTwoNetworkLogo,
  }: ProfileCardProps) {
    const query: Query = { login: login.toLowerCase() }
    if (cursus !== 'hide') query.cursus = cursus
    if (!showEmail) query.email = 'hide'
    if (darkTheme) query.dark = 'true'
    if (hideLeetLogo) query.leet_logo = 'hide'
    if (hideFortyTwoNetworkLogo) query.forty_two_network_logo = 'hide'
    const queryStringified = queryString.stringify(query)
    setCardImage(`/api/profile?${queryStringified}`)
  }
  return (
    <div>
      <h3 className="mb-5 text-xl font-bold">Profile Card Generator</h3>
      <div className="flex">
        <div className="mr-5">
          <img src={cardImage} width={450} />
          <p className="mt-5">
            Add the code bellow to your{' '}
            <code className="px-2 py-1 text-sm rounded bg-gray-50">
              README.md
            </code>{' '}
            file:
          </p>
          <div
            className="p-3 mt-2 overflow-x-auto font-mono text-xs rounded-lg select-all bg-gray-50"
            style={{ maxWidth: 450 }}
          >
            [![42 Profile Card](https://1337-readme.vercel.app{cardImage}
            [![42 Profile Card](https://1337-readme-xi.vercel.app{cardImage}
            )](https://github.com/mohouyizme/1337-readme)
          </div>
        </div>
