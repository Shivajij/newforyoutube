# newforyoutube



html


import { useState } from "react";

function Demo() {
  const [show, setShow] = useState(false);
  const youtubeLink = "https://www.youtube.com/watch?v=retd7nAn_Sw&t";

  const handlePlayButtonClick = () => {
    // Open YouTube video in a new window or navigate to the link directly
    window.open(youtubeLink, "_blank");
  };

  return (
    <>
      <div className={`lottery-container ${show ? "blurred" : ""}`}>
        <div
          className="winning-combination"
          style={{ display: "flex", flexDirection: "column" }}
        >
          <p style={{ fontSize: "22px" }}>Winning Combination</p>
          <div style={{ display: "flex" }}>
            <span className="rounded-number">05</span>
            <span className="rounded-number">21</span>
            <span className="rounded-number">29</span>
            <span className="rounded-number">12</span>
            <span className="rounded-number">04</span>
          </div>
        </div>
        <div className="total-prize">
          <p>Total Prize:</p>
          <h4>AED 154360</h4>
        </div>
        <div>
          <p>Total Winnings:</p>
          <h4>370</h4>
        </div>
        <div
          style={{
            display: "flex",
            flexDirection: "column",
            width: "50%",
            alignItems: "center",
          }}
        >
          <button className="view-history-btn" onClick={() => setShow(!show)}>
            VIEW ALL DRAW HISTORY
          </button>
          <p className="draw-date">FRI 23 FEB</p>
        </div>
      </div>

      {show && (
        <>
          <div className="overlay" onClick={() => setShow(false)}></div>
          <div
            className="main-popup"
            style={{
              border: "1px solid black",
              height: "60%",
              width: "60%",
              position: "fixed",
              top: "50%",
              left: "50%",
              transform: "translate(-50%, -50%)",
              display: "flex",
              justifyContent: "center",
              alignItems: "center",
              backgroundColor: "rgba(255, 182, 193, 0.9)",
            }}
          >
            <div className="child-popup">
              <iframe
                style={{
                  position: "fixed",
                  top: "50%",
                  left: "50%",
                  transform: "translate(-50%, -50%)",
                  display: "flex",
                  justifyContent: "center",
                  alignItems: "center",
                }}
                title="YouTube Video"
                width="350" // Adjust the width as needed
                height="310" // Adjust the height as needed
                src={`https://www.youtube.com/embed/${extractVideoId(
                  youtubeLink
                )}`}
                frameBorder="0"
                allowFullScreen
              ></iframe>
              <button onClick={() => setShow(false)}>Close</button>
            </div>
          </div>
        </>
      )}
    </>
  );
}

// Function to extract the video ID from a YouTube link
function extractVideoId(link) {
  const regex =
    /(?:https?:\/\/)?(?:www\.)?(?:youtube\.com\/(?:[^/]+\/.+\/|(?:v|e(?:mbed)?)\/|.*[?&]v=)|youtu\.be\/)([^"&?/\s]{11})/;
  const match = link.match(regex);
  return match && match[1];
}

export default Demo;







css


.lottery-container {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

.winning-combination {
  display: flex;
  align-items: center;
}

.rounded-number {
  background-color: #007bff;
  color: #fff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 10px;
  font-weight: bold;
}

.total-prize,
.total-winnings {
  font-size: 14px;
}

.view-history-btn {
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
  font-size: 14px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.view-history-btn:hover {
  background-color: #0056b3;
}

.draw-date {
  font-size: 12px;
  color: #888;
}
/* Demo.css */

.lottery-container {
  /* Your existing styles for lottery-container */
  position: relative;
  transition: filter 0.3s ease-out;
}

.blurred {
  filter: blur(3px); /* Adjust the blur strength as needed */
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5); /* Adjust the transparency as needed */
  z-index: 999;
}

.main-popup {
  /* Your existing styles for main-popup */
  z-index: 1000;
}

.child-popup {
  /* Your existing styles for child-popup */
}

/* Add any additional styles as needed */
