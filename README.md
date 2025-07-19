import React, { useState } from "react";
import {
  Container,
  Navbar,
  Nav,
  Form,
  Button,
  Row,
  Col,
  Card,
  InputGroup
} from "react-bootstrap";
import "bootstrap/dist/css/bootstrap.min.css";

function App() {
  const [panjang, setPanjang] = useState("");
  const [lebar, setLebar] = useState("");
  const [tinggi, setTinggi] = useState("");
  const [luas, setLuas] = useState("");

  const hitungLuas = () => {
    const p = parseFloat(panjang);
    const l = parseFloat(lebar);
    const t = parseFloat(tinggi);

    if (isNaN(p) || isNaN(l) || isNaN(t) || p <= 0 || l <= 0 || t <= 0) {
      setLuas("Input tidak valid");
      return;
    }

    const hasil = 2 * ((p * l) + (l * t) + (p * t));
    setLuas(`${hasil.toFixed(2)} cm²`);
  };

  return (
    <div style={{ backgroundColor: "#f8f9fa", minHeight: "100vh" }}>
      <Container className="text-center py-4">
        <img
          src="https://via.placeholder.com/80"
          alt="Logo"
          className="mb-2"
        />
        <h1 className="fw-bold">Judul Website</h1>
      </Container>

      <Navbar bg="light" expand="lg" className="shadow-sm">
        <Container>
          <Navbar.Toggle aria-controls="navbar-nav" />
          <Navbar.Collapse id="navbar-nav">
            <Nav className="mx-auto">
              <Nav.Link className="fw-semibold mx-3">HOME</Nav.Link>
              <Nav.Link className="fw-semibold mx-3">ABOUT</Nav.Link>
              <Nav.Link className="fw-semibold mx-3">CONTACT US</Nav.Link>
            </Nav>
          </Navbar.Collapse>
        </Container>
      </Navbar>

      <Container className="my-5">
        <Card className="p-4 shadow-sm border-0 rounded-4">
          <h2 className="text-center text-secondary fw-bold mb-4">
            Perhitungan Luas Permukaan Balok
          </h2>

          <Row className="mb-4 justify-content-center">
            <Col md={6}>
              <Form.Label className="fw-semibold">NIM:</Form.Label>
              <Form.Control placeholder="Masukkan NIM Anda" className="mb-3" />
            </Col>
          </Row>

          <Row className="mb-4">
            <Col md={4}>
              <Form.Group>
                <Form.Label className="fw-semibold">Panjang</Form.Label>
                <InputGroup>
                  <Form.Control
                    type="number"
                    value={panjang}
                    onChange={(e) => setPanjang(e.target.value)}
                    placeholder="cm"
                  />
                </InputGroup>
              </Form.Group>
            </Col>
            <Col md={4}>
              <Form.Group>
                <Form.Label className="fw-semibold">Lebar</Form.Label>
                <InputGroup>
                  <Form.Control
                    type="number"
                    value={lebar}
                    onChange={(e) => setLebar(e.target.value)}
                    placeholder="cm"
                  />
                </InputGroup>
              </Form.Group>
            </Col>
            <Col md={4}>
              <Form.Group>
                <Form.Label className="fw-semibold">Tinggi</Form.Label>
                <InputGroup>
                  <Form.Control
                    type="number"
                    value={tinggi}
                    onChange={(e) => setTinggi(e.target.value)}
                    placeholder="cm"
                  />
                </InputGroup>
              </Form.Group>
            </Col>
          </Row>

          <div className="d-grid gap-2 mb-4">
            <Button variant="primary" size="lg" onClick={hitungLuas} className="rounded-3">
              Hitung Luas Permukaan
            </Button>
          </div>

          <Row className="justify-content-center">
            <Col md={6}>
              <Form.Group>
                <Form.Label className="fw-semibold">Hasil Luas Permukaan</Form.Label>
                <Form.Control
                  type="text"
                  value={luas}
                  readOnly
                  className="fs-5 text-center border border-primary rounded-3 py-2"
                />
              </Form.Group>
            </Col>
          </Row>

          <div className="text-center mt-5 text-muted">
            Nama @copyright 2025
          </div>
        </Card>
      </Container>
    </div>
  );
}

export default App;
