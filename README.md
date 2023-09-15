import React, { useEffect, useState } from "react";
import {Link} from 'react-router-dom';
import './Champion.Grid.css'

function Champ() {
    const [champions, setChampions] = useState([]);

    useEffect(() => {
        fetch('http://ddragon.leagueoflegends.com/cdn/13.18.1/data/ko_KR/champion.json')
            .then(respon => respon.json())
            .then(data => setChampions(Object.values(data.data)))
    }, [])

    return (
        <>
            <h1>챔피언 목록</h1>
            <div className="champ-grid">
                {champions.map(champion => (
                    <Link to={`/champions/${champion.id}`} key={champion.key} className=".champ-link">
                        <img src={`http://ddragon.leagueoflegends.com/cdn/img/champion/loading/${champion.id}_0.jpg`} alt="{champion.name}" style={{width:'120px', height:'100px'}}/>
                        {champion.name}
                    </Link>
                ))}
            </div>
        </>
    )
}

export default Champ;# LoL
게임활용
